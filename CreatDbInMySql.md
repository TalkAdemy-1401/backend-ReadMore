2. ایجاد یک پایگاه داده نمونه
   
      پایگاه داده MySQL را دانلود و آن را در یک محل قابل دسترس نصب کنید. اکنون می‌خواهیم برای استفاده از MySQL به منظور اتصال و اجرای کوئری‌ها، یک پایگاه داده نمونه بسازیم. در ابتدا، باید با استفاده از یک «کلاینت» (Client) دلخواه به پایگاه داده متصل شد و با اجرای دستورات زیر، پایگاه داده نمونه را ایجاد کرد.
      
      <div dir="ltr">
         
      ```sql	
      create database sample;
      ```
         
      </div>
   
      علاوه بر این، برای اتصال به پایگاه داده به نام کاربری و کلمه عبور نیاز خواهد بود؛ مگر اینکه بخواهید به عنوان ادمین این ارتباط را برقرار کنید (معمولاً چنین کاری توصیه نمی‌شود). کد زیر، یک کاربر با نام «testuser» را ایجاد می‌کند که می‌تواند با استفاده از کلمه عبور «securepwd» و از طریق ماشینی که پایگاه داده MySQL در آن اجرا می‌شود (localhost)، اتصال را برقرار کند.
   
      <div dir="ltr">
         
      ```sql	
      create user 'testuser'@'localhost' identified by 'securepwd';
      ```
         
      </div>
   
      اگر قصد دارید به پایگاه داده‌ای متصل شوید که در یک ماشین دیگر (remotemc) اجرا می‌شود، باید از کد زیر استفاده کنید (عبارت remotemc می‌تواند نام یک سرویس میزبان یا یک آدرس آی‌پی باشد):

      <div dir="ltr">
         
      ```sql	
      create user 'testuser'@'localhost' identified by 'securepwd';
      ```
         
      </div>
   
      پس از ایجاد نام کاربری و کلمه عبور، باید مجوز دسترسی به این پایگاه داده نمونه اعطا شود.
   
      <div dir="ltr">
         
      ```sql	
      grant all on sample.* to 'testuser'@'localhost';
      ```
         
      </div>   
      
      اگر پایگاه داده در جای دیگری قرار دارد، باید از کد زیر استفاده شود:
   
      <div dir="ltr">
         
      ```sql	
      grant all on sample.* to 'testuser'@'remotemc';
      ```
         
      </div>   
   
      حال باید اتصال به پایگاه داده توسط نام کاربری و کلمه عبوری ایجاد شده را تأیید کنید. به علاوه، با استفاده از اجرای دستورات زیر بعد از اتصال، می‌توانید از صحیح بودن مجوزها مطمئن شوید.

      <div dir="ltr">
         
      ```sql	
      create table joe(id int primary key auto_increment, name varchar(25));
      drop table joe;
      ```
         
      </div> 
