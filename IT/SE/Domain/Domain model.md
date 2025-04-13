# Discount domain
Coupon, Promotional code, Voucher
- Coupon code is **system-generated code** 
- Promotional code is a code offered by retailers

- Coupon is a document or certificate to discount
- Coupon gives you a discount; voucher gives you the item; gift card = is redeemed at its cash value (or for particular item).
## Coupon code
#promo-code, #coupon, #discount, #voucher 
```javascript
class CouponCode {
	code: string
	discountType: [FixedAmount, Percentage]
	applicableServices: List<Service>
	applicableUser: List<User>
}
```
- Thường không thể sử dụng nhiều mã giảm giá cùng lúc
- Non-transferable
- Type of discounts
	- Fixed amount off
	- Percentage off
	- Free shipping
	- Buy one get one free, etc
- Restriction conditions
	- Minimum purchase amount
	- Maximum discount limit
	- Specific product category
	- Single use per customer
## Giftcard
```javascript
class GiftCard {
	type: [Physical, Digital]
}
```
- Prepaid cards.
- Có thể sử dụng nhiều lần cho tới khi hết số dư.
- Người dùng có thể được lựa chọn nhiều product hơn.
- Có thể làm quà tặng
## Cashback
- Hoàn tiền

# Reference
- [Quora](https://www.quora.com/What-is-the-difference-between-coupon-codes-and-gift-cards-I-know-gift-cards-are-hard-real-things-and-coupons-are-just-codes-but-are-there-any-other-differences)
- 