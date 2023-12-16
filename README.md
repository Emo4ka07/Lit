# Lit
Система, позволяющая пользователям публиковать собственное литературное творчество, читать и комментировать публикации других пользователей
# Пользовательские сценарии
1)	Неавторизованный пользователь переходит на сайт, отображается главная страница со ссылками на вход и регистрацию и с последними публикациями, по ссылке в названии можно перейти к полной версии публикации и ознакомиться с комментариями.
2)	Незарегистрированный пользователь переходит на сайт, по ссылке с главной страницы переходит на форму регистрации, при успешной регистрации переходит на главную страницу. В публикациях появляется возможность оставлять комментарии, на главной странице появляется ссылка на личный кабинет с возможностью добавлять собственные публикации.
3)	Модератор может удалять публикации и комментарии, нарушающие правила ресурса.
# Интерфейс
![image](https://github.com/Emo4ka07/Lit/assets/154008787/4229babc-7060-4292-a763-1d19e10c1693)
# UML диаграммы
![image](https://github.com/Emo4ka07/Lit/assets/154008787/0c7f5a7d-0fb2-4511-8f4b-be256c29c0b5)
sequenceDiagram
    participant "User" as User
    participant "Main Page" as MainPage
    participant "Publication" as Publication
    participant "Registration Form" as RegistrationForm
    participant "Personal Account" as PersonalAccount
    participant "Login Page" as LoginPage
    participant "Authentication System" as AuthSystem

    activate User
    User->MainPage: Visit site
    activate MainPage
    MainPage-->User: Display main page with links to login, registration, and latest publications

    User->Publication: Click on publication title
    activate Publication
    Publication-->User: Display full version of publication and comments
    deactivate Publication

    User->RegistrationForm: Click on registration link
    activate RegistrationForm
    RegistrationForm-->User: Display registration form

    User->RegistrationForm: Fill in registration details
    User->RegistrationForm: Submit registration form
    RegistrationForm-->User: Successful registration
    RegistrationForm-->MainPage: Redirect to main page after registration
    deactivate RegistrationForm

    MainPage-->User: Main page with comment capability and link to personal account
    deactivate MainPage

    User->PersonalAccount: Click on personal account link
    activate PersonalAccount
    PersonalAccount-->User: Display personal account page with option to add publications

    User->PersonalAccount: Add own publication
    PersonalAccount-->User: Publication added successfully
    deactivate PersonalAccount

    User->MainPage: Visit site
    activate MainPage
    MainPage-->User: Display main page with links to login, registration, and latest publications
    deactivate MainPage

    User->LoginPage: Click on login link
    activate LoginPage
    LoginPage-->User: Display login form

    alt Incorrect password entered
        User->LoginPage: Enter incorrect password
        LoginPage->AuthSystem: Authenticate User
        activate AuthSystem
        AuthSystem-->LoginPage: Incorrect Password
        LoginPage-->User: Display error message
        deactivate AuthSystem
    else Correct password entered initially
        User->LoginPage: Enter correct password
        LoginPage->AuthSystem: Authenticate User
        activate AuthSystem
        AuthSystem-->LoginPage: Successful Authentication
        LoginPage-->User: Redirect to user's page
        deactivate AuthSystem
    end
    deactivate LoginPage
    
