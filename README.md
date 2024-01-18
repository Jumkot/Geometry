Приложение принимает на вход окружности в WKT-подобном формате.

Для каждой фигуры приложение определяет:
1. Периметр.
2. Площадь.
3. С какими фигурами пересекается текущая.

# Грамматика (EBNF):

Object = 'circle' '(' Point ',' Number ')'

Point = Number Number

Number = (* Floating-point number *)

# Дополнительные замечания:
* Типы фигур нечувствительны к регистру (case insensitive).
* Между токенами может быть произвольное количество пробельных символов.
* Одна фигура занимает ровно одну строку. В строке не может быть нескольких фигур.

# Входные и выходные данные:
Ввод:
> circle(0 0, 1.5)
> 
> Circle(0 1, 1.5)

Вывод:
> 1. circle(0 1, 1.5)
>    
>     perimeter = 9.4247
>    
>     area = 7.0686
>    
>     intersects:
>    
>       2.. circle
> 
> 3. circle(0 0, 1.5)
>    
>     perimeter = 9.4247
>    
>     area = 7.0686
>    
>     intersects:
>    
>       1.. circle

Приложение должно обрабатывать некорректные входные данные и выводить сообщения об ошибках. Примеры:

> circlee(1.0 2.0, 3)
> 
> ^
> 
> Error at column 0: expected 'circle'

> circle(x1 2, 3.0)
> 
>       ^
>        
> Error at column 7: expected '\<double\>'

> circle(1 2, 3.1(
> 
>               ^
> 
> Error at column 15: expected ')'

> circle(1.0 2.1, 3) 123
> 
>                  ^
> 
> Error at column 19: unexpected token
