# showing-the-code-snippet-for-UPDATE-test-case-
def test_update_product(self):
    # Create a product
    product = Product(name="OldName", category="OldCategory", available=True)
    product.save()
    
    # Send a PUT request to update the product
    response = self.client.put(f"/products/{product.id}", json={"name": "NewName", "category": "NewCategory"})
    
    # Assert that the product details were updated
    assert response.status_code == 200
    updated_product = Product.find(product.id)
    assert updated_product.name == "NewName"
    assert updated_product.category == "NewCategory"
