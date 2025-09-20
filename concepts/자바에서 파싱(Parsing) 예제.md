# 자바에서 파싱(Parsing) 예제

## 1. 문자열을 숫자로 파싱

문자열 `"123"`을 정수로 변환

``` java
public class ParseIntExample {
    public static void main(String[] args) {
        String number = "123";
        int value = Integer.parseInt(number);   // 문자열 → int
        System.out.println(value + 10);         // 133
    }
}
```

-   `Integer.parseInt()` 가 문자열을 숫자 데이터로 **파싱**한다.

------------------------------------------------------------------------

## 2. CSV 한 줄 파싱

쉼표로 구분된 문자열을 배열로 변환

``` java
public class CsvParsingExample {
    public static void main(String[] args) {
        String line = "Amy,30,Developer";
        String[] parts = line.split(",");    // CSV 파싱
        String name = parts[0];
        int age = Integer.parseInt(parts[1]);
        String job = parts[2];
        System.out.printf("%s (%d) - %s%n", name, age, job);
    }
}
```

------------------------------------------------------------------------

## 3. JSON 파싱 (Jackson 사용)

JSON 텍스트를 객체로 변환

``` java
import com.fasterxml.jackson.databind.ObjectMapper;

public class JsonParsingExample {
    public static void main(String[] args) throws Exception {
        String json = "{\"name\":\"Amy\",\"age\":30}";

        ObjectMapper mapper = new ObjectMapper();
        Person person = mapper.readValue(json, Person.class); // 파싱
        System.out.println(person.getName() + " - " + person.getAge());
    }
}

class Person {
    private String name;
    private int age;
    // getter/setter 생략
}
```

-   `ObjectMapper.readValue`가 JSON 문자열을 `Person` 객체로
    **파싱**한다.

------------------------------------------------------------------------

## 4. XML 파싱 (DOM 방식)

XML 문서를 DOM 트리로 읽어오기

``` java
import javax.xml.parsers.*;
import org.w3c.dom.*;

public class XmlParsingExample {
    public static void main(String[] args) throws Exception {
        String xml = "<user><name>Amy</name><age>30</age></user>";
        DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
        DocumentBuilder builder = factory.newDocumentBuilder();
        Document doc = builder.parse(new java.io.ByteArrayInputStream(xml.getBytes()));

        String name = doc.getElementsByTagName("name").item(0).getTextContent();
        String age  = doc.getElementsByTagName("age").item(0).getTextContent();
        System.out.println(name + " - " + age);
    }
}
```

------------------------------------------------------------------------

## 핵심

-   파싱은 **문자열 → 의미 있는 데이터 구조** 변환
-   자바에서는 `parseInt`, `split`, Jackson, Gson, DOM/SAX 등 다양한
    라이브러리로 파싱을 수행
