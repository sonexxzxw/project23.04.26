# project23.04.26
## 1.telegram чат-бот (пайтон і аіограм)
-  основна ідея: допомагає фрілансеру швидко порахувати фінальну ціну проєкту, враховуючи годинни роботи, складність і комісію платформи
## 2. основнй функціонал
- приймати відкористувача кількість годин тапогодинну ставку
- вираховувати суму з урахуванням податку(5%) та комісії сервісу(20%)
- виводити деталізований чек повідомленням
## 3. структура данних 
|назва змінної|тип данних|для чого потрібна|
|:--- |:--- |--- |
|hourly_rate|float|погдинна ставка користувача|
|hours_spent|int|кількість втраченихгодин|
|total_price|float|результат після всіх математичних операцій|
|is_active|bool|контроль стану сесії бота|

import flet as ft

def main(page: ft.Page):
    page.title = "Мій Проєкт: Task Master"
    page.theme_mode = ft.ThemeMode.DARK
    page.window_width = 1000
    page.window_height = 700
    page.padding = 0
    page.spacing = 0
    layout = ft.Row(
        expand=True,
        spacing=0,
        controls=[
            ft.Container(
                width=300,
                bgcolor=ft.colors.BLUE_GREY_900,
                padding=20,
                content=ft.Column(
                    controls=[
                        ft.Text("TASK MASTER", size=24, weight=ft.FontWeight.BOLD, color=ft.colors.BLUE_400),
                        ft.Divider(height=20, color=ft.colors.TRANSPARENT),
                        ft.ListTile(leading=ft.Icon(ft.icons.INBOX), title=ft.Text("Вхідні")),
                        ft.ListTile(leading=ft.Icon(ft.icons.CALENDAR_TODAY), title=ft.Text("Сьогодні")),
                        ft.ListTile(leading=ft.Icon(ft.icons.STAR), title=ft.Text("Важливе")),
                        ft.ListTile(leading=ft.Icon(ft.icons.SETTINGS), title=ft.Text("Налаштування")),
                    ]
                )
            ),
            
            ft.Container(
                expand=True,
                bgcolor=ft.colors.BLACK12,
                padding=20,
                content=ft.Column(
                    controls=[
                        ft.Row(
                            alignment=ft.MainAxisAlignment.SPACE_BETWEEN,
                            controls=[
                                ft.Text("Сьогоднішні справи", size=20, weight=ft.FontWeight.W_500),
                                ft.Icon(ft.icons.MORE_VERT)
                            ]
                        ),
                        
                        ft.Container(expand=True), 
                        
                        ft.Row(
                            controls=[
                                ft.TextField(
                                    hint_text="Додати нове завдання...", 
                                    expand=True,
                                    border_radius=10
                                ),
                                ft.IconButton(
                                    icon=ft.icons.ADD_CIRCLE, 
                                    icon_color=ft.colors.BLUE_400,
                                    icon_size=40
                                )
                            ]
                        )
                    ]
                )
            )
        ]
    )

    page.add(layout)

ft.app(target=main)
