---
title: "範圍解析運算子：:: | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "::"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ":: 運算子"
  - "運算子 [C++], 範圍解析"
  - "範圍解析運算子"
  - "範圍, 範圍解析運算子"
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 範圍解析運算子：::
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

範圍解析運算子 `::` 可用來識別及區分不同範圍內使用的識別項。  如需範圍的詳細資訊，請參閱 [範圍](../cpp/scope-visual-cpp.md)。  
  
## 語法  
  
```  
:: identifier class-name :: identifier namespace :: identifier enum class :: identifier enum struct :: identifier  
```  
  
## 備註  
 `identifier` 可以是變數、函式或列舉值。  
  
## 搭配類別和命名空間  
 下列範例顯示範圍解析運算子如何與命名空間和類別搭配使用：  
  
```cpp  
namespace NamespaceA{  
    int x;  
    class ClassA {  
    public:  
        int x;  
    };  
}  
  
int main() {  
  
    // A namespace name used to disambiguate  
    NamespaceA::x = 1;  
  
    // A class name used to disambiguate  
    NamespaceA::ClassA a1;  
    a1.x = 2;  
  
}  
  
```  
  
 不含範圍限定詞的範圍解析運算子是指全域命名空間。  
  
```cpp  
namespace NamespaceA{  
    int x;  
}  
  
int x;   
  
int main() {  
    int x;  
  
    // the x in main()  
    x = 0;   
    // The x in the global namespace  
    ::x = 1;   
  
    // The x in the A namespace  
    NamespaceA::x = 2;   
}  
```  
  
 您可以使用範圍解析運算子來識別命名空間的成員，或識別在使用指示詞中指定成員命名空間的命名空間。  在下面的範例中，即使已在命名空間 `NamespaceB` 中宣告 `ClassB`，您還是可以使用 `NamespaceC` 來限定 `ClassB`，因為使用指示詞已在 `NamespaceC` 中指定 `NamespaceB`。  
  
```cpp  
namespace NamespaceB {  
    class ClassB {  
    public:  
        int x;  
    };  
}  
  
namespace NamespaceC{  
    using namespace B;  
  
}  
int main() {  
    NamespaceB::ClassB c_b;  
    NamespaceC::ClassB c_c;  
  
    c_b.x = 3;  
    c_c.x = 4;  
}  
  
```  
  
 您可以使用範圍解析運算子的鏈結。  在下列範例中，`NamespaceD::NamespaceD1` 會識別巢狀命名空間 `NamespaceD1`，而 `NamespaceE::ClassE::ClassE1` 會識別巢狀類別 `ClassE1`。  
  
```cpp  
namespace NamespaceD{  
    namespace NamespaceD1{  
        int x;  
    }  
}  
  
namespace NamespaceE{  
  
    class ClassE{  
    public:  
        class ClassE1{  
        public:  
            int x;  
        };  
    };  
}  
  
int main() {  
    NamespaceD:: NamespaceD1::x = 6;  
    NamespaceE::ClassE::ClassE1 e1;  
    e1.x = 7  ;  
}  
  
```  
  
## 搭配靜態成員  
 您必須使用範圍解析運算子來呼叫類別的靜態成員。  
  
```cpp  
class ClassG {  
public:  
    static int get_x() { return x;}  
    static int x;  
};  
  
int ClassG::x = 6;  
  
int main() {  
  
    int gx1 = ClassG::x;  
    int gx2 = ClassG::get_x();   
}  
  
```  
  
## 搭配限定範圍的列舉  
 範圍解析運算子也可以與限定範圍的列舉值[列舉宣告](../cpp/enumerations-cpp.md)搭配使用，如下列範例所示：  
  
```cpp  
enum class EnumA{  
    First,  
    Second,  
    Third  
};  
  
int main() {  
  
    EnumA enum_value = EnumA::First;  
}  
  
```  
  
## 請參閱  
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [命名空間](../cpp/namespaces-cpp.md)   
 [名稱和限定名稱](../misc/names-and-qualified-names.md)