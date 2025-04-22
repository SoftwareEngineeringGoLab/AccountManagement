# مدیریت حساب بانکی


# بخش اول

## پرسش اول
در این کد چه خطایی وجود دارد؟ و به نظر شما چرا دیده نشده‌است؟


در این کد، خطایی وجود دارد که اجازه می‌دهد برداشت از حساب حتی زمانی که موجودی کافی نیست انجام شود و منجر به منفی شدن موجودی حساب می‌گردد. این سناریو در تست های فعلی بررسی نشده و برای همین تست ها به درستی پاس می‌شوند و کسی توجهش به خطای موجود جلب نشده است.


## پرسش دوم
پس از یافتن خطا، یک آزمون برای آن بنویسید که منجر به کشف آن خطا شود. سپس آن را به گونه‌ای اصلاح کنید که آن مورد آزمون، پاس شود.

آزمون جدیدی اضافه می‌کنیم که در آن تراکنش‌ها بتوانند موجودی را منفی کنند. در حالت عادی این تست پاس نمی‌شود.

<img width="1512" alt="1-fail" src="https://github.com/user-attachments/assets/bee44c0b-a246-4cb6-8a8c-158690c31876" />


سپس با تغییر کد به صورتی تغییر می‌دهیم که اجازه ندهد موجودی منفی شود و برای این تراکنش ها یک خطا چاپ کند.
```java
public static int calculateBalance(List<Transaction> transactions) {
    int balance = 0;
    for (Transaction t : transactions) {
        if (t.getType() == TransactionType.DEPOSIT) {
            balance += t.getAmount();
        } else if (t.getType() == TransactionType.WITHDRAWAL) {
            if (balance >= t.getAmount()) {
                balance -= t.getAmount();
            } else {
                System.out.print("Transaction cannot be finished!");
            }
        }

    }
    return balance;
}
```

و سپس مشاهده می‌شود که تست جدید ما پاس می‌شود و این خطا برطرف شده است.

<img width="1512" alt="1-pass" src="https://github.com/user-attachments/assets/2d45d890-4fa0-4354-bdc1-2d1416e911aa" />

