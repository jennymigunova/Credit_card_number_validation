## Отчёт о тестировании Credit Card Number Validator

### Краткое описание
01.03.2021 - 03.03.2021 было проведено функциональное тестирование приложения Credit Card Number Validator.

На тестирование затрачено: 1 час

### В результате тестирования выявлены следующие дефекты:

[При вводе валидных значений карты программа показывает, что карта невалидна](https://github.com/jennymigunova/Credit_card_number_validation/issues/2)

### Описание процесса тестирования
В процессе тестирования использовались следующие артефакты:

- [Руководство по установке IntelliJ IDEA](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/idea.md)
```java 
  public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```
### В качестве тестовых данных использовались данные [freeformatter.com](freeformatter.com):

1. VISA:
- 4485536442542964
- 4485173528369920
- 4114295960215203617
2. MasterCard:
- 2221006703746889
- 2221003951320269
- 5458745083157541
3. American Express (AMEX):
- 371460155374520
- 347365156202896
- 340650818184096
4.Discover:
- 6011347979536843
- 6011065034900313
- 6011243814507469023
5. JCB:
- 3540911987913794
- 3589558450897491
- 3534507562263632012

### Тестирование производилось в следующем окружении:

MacOS Version 11.1 , 32 bit
Java 11
IntelliJ IDEA 2020.3