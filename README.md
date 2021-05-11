# Memorytrain API 

## 단어장을 저장하고 암기하는 사이트입니다. 회원제로 운영됩니다.

1. 회원가입

   - http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/rest-auth/signup/

     URL 에 POST 방식으로

     email, name, password, confirm_password 

     를 body에 붙여 보낸다.

     - 예시)  

       curl --location --request POST 'http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/rest-auth/signup/' \

       --header 'Cookie: sessionid=72o41h01re764ppt2qkfp0xgcto5c6s1; csrftoken=2MArAS0Fl7cGJqFIT7JiKV9n55AAFs4yfntM1yC7ACBYCyeOB5bQPFvyLJpwe0nI' \

       --form 'email="test1@test.com"' \

       --form 'name="test"' \

       --form 'password="test1234"' \

       --form 'confirm_password="test1234"'

2. 로그인

   - http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/rest-auth/login/

     에 POST 방식으로

     email과 password

     를 body에 붙여보낸다.

     - 예시 ) 

       curl --location --request POST 'http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/rest-auth/login/' \

       --header 'Cookie: csrftoken=RC1upoDQiMiRtMdWr4PMGw9oP9idfeoz8tmQalkF68yCU6zkNKNg821darfgSkV7; sessionid=3gi2wjlfnqojsgugfonjqj5wovrp0ir8' \

       --form 'email="test1@test.com"' \

       --form 'password="test1234"'



3. 단어책 만들기

   - http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/books/create/

     에 POST 방식으로

     header에 

     Authorization: JWT {2번에서 response로 받은 token 값}

     을 붙이고

     body에 JSON 형식으로

     {   

       "title":"pip 테스트", 

       "description":"테스트" ,

       "cards":[{"word":"apple", "meaning":"사과라는 뜻"}, {"word":"banana", "meaning":"바나나라는 뜻"}]

     }

     를 붙여  보낸다.

     - 예시)

       curl --location --request POST 'http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/books/create/' \

       --header 'Authorization: JWT eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjozLCJ1c2VybmFtZSI6InRlc3QxQHRlc3QuY29tIiwiZXhwIjoxNjIwNzI4ODEyLCJlbWFpbCI6InRlc3QxQHRlc3QuY29tIiwib3JpZ19pYXQiOjE2MjA3MjUyMTJ9.f2KguIe0sTFpksnIVD0DEZtUiqBHvxGat4sxCglq3jM' \

       --header 'Content-Type: application/json' \

       --header 'Cookie: csrftoken=RC1upoDQiMiRtMdWr4PMGw9oP9idfeoz8tmQalkF68yCU6zkNKNg821darfgSkV7; sessionid=3gi2wjlfnqojsgugfonjqj5wovrp0ir8' \

       --data-raw '{   

         "title":"pip 테스트", 

         "description":"테스트" ,

         "cards":[{"word":"apple", "meaning":"사과라는 뜻"}, {"word":"banana", "meaning":"바나나라는 뜻"}]

       }'

       

4. 단어책 가져오기

   - http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/books/1/

     과 같이 뒤에 가져오고자하는 단어책의 id를 붙이고

     GET 방식으로

     header에 

     Authorization: JWT {2번에서 response로 받은 token 값}

     을 붙여 보낸다.

     - 예시 ) 

       curl --location --request GET 'http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/books/1/' \

       --header 'Authorization: JWT eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjozLCJ1c2VybmFtZSI6InRlc3QxQHRlc3QuY29tIiwiZXhwIjoxNjIwNzI4ODEyLCJlbWFpbCI6InRlc3QxQHRlc3QuY29tIiwib3JpZ19pYXQiOjE2MjA3MjUyMTJ9.f2KguIe0sTFpksnIVD0DEZtUiqBHvxGat4sxCglq3jM' \

       --header 'Cookie: csrftoken=RC1upoDQiMiRtMdWr4PMGw9oP9idfeoz8tmQalkF68yCU6zkNKNg821darfgSkV7; sessionid=3gi2wjlfnqojsgugfonjqj5wovrp0ir8'

     

   


5. 단어책 삭제하기

   - http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/books/2/

     에 DEL 방식으로 

     header에 

     Authorization: JWT {2번에서 response로 받은 token 값}

     을 붙여 보낸다.

     - 예시)

       curl --location --request DELETE 'http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/books/2/' \

       --header 'Authorization: JWT eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjozLCJ1c2VybmFtZSI6InRlc3QxQHRlc3QuY29tIiwiZXhwIjoxNjIwNzI4ODEyLCJlbWFpbCI6InRlc3QxQHRlc3QuY29tIiwib3JpZ19pYXQiOjE2MjA3MjUyMTJ9.f2KguIe0sTFpksnIVD0DEZtUiqBHvxGat4sxCglq3jM' \

       --header 'Cookie: csrftoken=RC1upoDQiMiRtMdWr4PMGw9oP9idfeoz8tmQalkF68yCU6zkNKNg821darfgSkV7; sessionid=3gi2wjlfnqojsgugfonjqj5wovrp0ir8'

       

6. 로그아웃하기

   - http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/rest-auth/logout/

     에 GET 방식으로 

     header에 

     Authorization: JWT {2번에서 response로 받은 token 값}

     을 붙여 보낸다.

     - 예시)

       curl --location --request GET 'http://dyphi-django-env.eba-kfhpwhqw.us-west-2.elasticbeanstalk.com/api/rest-auth/logout/' \

       --header 'Authorization: JWT eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjozLCJ1c2VybmFtZSI6InRlc3QxQHRlc3QuY29tIiwiZXhwIjoxNjIwNzI4ODEyLCJlbWFpbCI6InRlc3QxQHRlc3QuY29tIiwib3JpZ19pYXQiOjE2MjA3MjUyMTJ9.f2KguIe0sTFpksnIVD0DEZtUiqBHvxGat4sxCglq3jM' \

       --header 'Cookie: csrftoken=RC1upoDQiMiRtMdWr4PMGw9oP9idfeoz8tmQalkF68yCU6zkNKNg821darfgSkV7'

  
