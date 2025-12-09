---
title: "Sample App: In-App Purchase Recommendation"
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

## Exercise: In-App Purchase Recommendation

Build a Lambda function that receives a list of purchased items and returns recommendations for unpurchased items (simple set subtraction).

### Input Requirements

```json
{
  "allItems": ["starter_pack","booster_pack","data_pack","golden_apples","skins"],
  "owned": ["data_pack","starter_pack"]
}
```

### Processing

- Use sets to get the remaining items: `suggestions = allItems - owned`.  
- Return JSON `{ "suggestions": [...] }` with status 200.  
- Log input/output for easy debugging.

### Testing

- In console: create test event with multiple `owned` values.  
- Via API Gateway: `POST /suggest` with JSON body as above. 
![image](/images/5-Workshop/5.5-Sample-app/curl_post.png)
- Try error cases: missing `allItems` or `owned` → return 400 with clear message.
![image](/images/5-Workshop/5.5-Sample-app/Missing.png)
