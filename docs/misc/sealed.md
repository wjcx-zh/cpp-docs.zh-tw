---
title: "__sealed | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__sealed_cpp"
  - "__sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sealed 關鍵字 [C++]"
  - "__sealed 關鍵字"
ms.assetid: 9e5f778a-4ad8-468d-9c44-783e576fb49b
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __sealed
> [!NOTE]
>  本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 請參閱 [sealed](../windows/sealed-cpp-component-extensions.md) 如需新語法中使用的相同功能。  
  
 避免方法遭到覆寫或類別成為基底類別。  
  
## 語法  
  
```  
  
__sealed   
class-specifier  
__sealed   
struct-specifier  
__sealed   
function-declarator  
  
```  
  
## 備註  
 `__sealed` 關鍵字會指定不可覆寫類別方法，或類別不能是基底類別。  
  
 使用 `__sealed` 關鍵字時，請注意下列幾點：  
  
-   不可覆寫 `__sealed` 虛擬方法。  
  
-   如果非虛擬成員方法標記為 `__sealed`，則會忽略 `__sealed` 限定性條件。  
  
-   `__sealed` 方法不可為純方法。  
  
-   **\_\_Sealed** 搭配使用時，不允許關鍵字 [\_\_interface](../cpp/interface.md) 關鍵字。  
  
 當類別 \(或結構\) 具有 `__sealed` 標記時，類別不能當做基底類別使用。 例如：  
  
```  
__sealed __gc class A {  
   // ...  
};  
// error: cannot derive from a sealed class  
__gc class B : public A { /* ...*/ };  
```  
  
> [!NOTE]
>  不允許使用 `__sealed` 關鍵字搭配 `__abstract` 關鍵字。  
  
## 範例  
 下列範例中會宣告 sealed 虛擬方法 \(`f`\)。 然後在 `main()` 中覆寫函式，造成編譯器錯誤：  
  
```  
// keyword__sealed.cpp  
// compile with: /clr:oldSyntax  
  
#using <mscorlib.dll>  
extern "C" int printf_s(const char*, ...);  
  
__gc struct I  
{  
    __sealed virtual void f()  
    {   
        printf_s("I::f()\n");   
    }  
    virtual void g()  
    {  
        printf_s("I::g()\n");  
    }  
};  
  
__gc struct A : I   
{  
    void f() // C3248 sealed function  
    {   
        printf_s("A::f()\n");   
    }     
    void g()  
    {  
        printf_s("A::g()\n");  
    }  
};  
  
int main()  
{  
    A* pA = new A;  
  
    pA->f();  
    pA->g();  
}  
```