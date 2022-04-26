---
marp: true
---
# 코틀린 코드 문서화 (KDoc, Dokka)

---

## KDoc
코틀린 코드에 사용하는 문서화 주석의 형식이다.

```kotlin
/**
 * A group of *members*. [요약]
 * 
 * This class has no useful logic; it's just a documentation example. [상세 설명]
 *
 * @param T the type of a member in this group.
 * @property name the name of this group.
 * @constructor Creates an empty group.
 */
class Group<T>(val name: String) {
    /**
     * Adds a [member] to this group.
     * @return the new size of the group.
     */
    fun add(member: T): Int { ... }
}
```

---
![](exam_doc1.png)

---
## Dokka
KDoc을 읽어서 문서 생성을 해주는 도구이다.  
문서 출력 형식은 html, markdown 등이 있다.  

gradle, maven 등에서 사용할 수 있는 플러그인 형태로 제공된다.  

---
#### 1. 플러그인 추가
build.gradle.kts
```kotlin
plugins {
    id("org.jetbrains.dokka") version "1.6.21"
}

repositories {
    mavenCentral()
}
```

#### 2. 문서 생성하기 (dokka${format})
```shell
./gradlew dokkaHtml
```

생성된 문서는 별도로 경로를 지정하지 않는다면
build\\dokka\\html 에서 확인할 수 있다.

---

![[Pasted image 20220427062544.png]]

---
Referecnes

[Document Kotlin code: KDoc and Dokka | Kotlin (kotlinlang.org)](https://kotlinlang.org/docs/kotlin-doc.html)

[Gradle - Dokka (kotlin.github.io)](https://kotlin.github.io/dokka/1.6.10/user_guide/gradle/usage/)
