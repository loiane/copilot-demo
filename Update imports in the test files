package com.loiane.copilotdemo;

import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.AutoConfigureMockMvc;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.boot.test.mock.mockito.MockBean;
import org.springframework.http.MediaType;
import org.springframework.test.web.servlet.MockMvc;

import java.util.Arrays;
import java.util.List;

import static org.hamcrest.Matchers.hasSize;
import static org.mockito.BDDMockito.given;
import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.content;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.jsonPath;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;

import com.loiane.copilotdemo.product.Product;
import com.loiane.copilotdemo.product.ProductService;

@SpringBootTest
@AutoConfigureMockMvc
class CopilotDemoApplicationTests {

	@Autowired
	private MockMvc mockMvc;

	@MockBean
	private ProductService productService;

	@Test
	void contextLoads() {
	}

	@Test
	void shouldReturnListOfProducts() throws Exception {
		Product product1 = new Product();
		product1.setId(1L);
		product1.setName("Test Product 1");
		product1.setDescription("Description for product 1");
		product1.setPrice(java.math.BigDecimal.valueOf(10.00));

		Product product2 = new Product();
		product2.setId(2L);
		product2.setName("Test Product 2");
		product2.setDescription("Description for product 2");
		product2.setPrice(java.math.BigDecimal.valueOf(20.00));

		List<Product> allProducts = Arrays.asList(product1, product2);

		given(productService.findAllProducts()).willReturn(allProducts);

		mockMvc.perform(get("/api/products")
				.contentType(MediaType.APPLICATION_JSON))
				.andExpect(status().isOk())
				.andExpect(content().contentTypeCompatibleWith(MediaType.APPLICATION_JSON))
				.andExpect(jsonPath("$", hasSize(2)))
				.andExpect(jsonPath("$[0].name").value(product1.getName()))
				.andExpect(jsonPath("$[1].name").value(product2.getName()));
	}
}
