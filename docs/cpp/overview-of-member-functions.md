---
title: "成員函式概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內嵌函式, 將成員函式視為"
  - "成員函式, 類別宣告中的定義"
  - "非靜態成員函式"
  - "this 指標, 和非靜態成員函式"
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 成員函式概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

成員函式不是靜態就是非靜態。  由於靜態成員函式沒有隱含的 **this** 引數，因此靜態成員函式的行為會與其他成員函式不同。  非靜態成員函式具有 **this** 指標。  無論是靜態或非靜態的成員函式，都可以在類別宣告之內或之外定義。  
  
 如果成員函式是在類別宣告內定義，則會將它視為內嵌函式，而且不需要使用其類別名稱限定函式名稱。  雖然在類別宣告內定義的函式已視為內嵌函式，但是您可以使用 **inline** 關鍵字記載程式碼。  
  
 以下是在類別宣告內宣告函式的範例：  
  
```  
// overview_of_member_functions1.cpp  
class Account  
{  
public:  
    // Declare the member function Deposit within the declaration  
    //  of class Account.  
    double Deposit( double HowMuch )  
    {  
        balance += HowMuch;  
        return balance;  
    }  
private:  
    double balance;  
};  
  
int main()  
{  
}  
```  
  
 如果成員函式的定義是在類別宣告之外，則只有在該函式明確宣告為 **inline** 時，才會將它視為內嵌函式。  此外，定義中的函式名稱必須使用範圍解析運算子 \(`::`\) 以其類別名稱加以限定。  
  
 下列範例與上述 `Account` 類別宣告相同，唯一的差異在於 `Deposit` 函式是在類別宣告之外定義：  
  
```  
// overview_of_member_functions2.cpp  
class Account  
{  
public:  
    // Declare the member function Deposit but do not define it.  
    double Deposit( double HowMuch );  
private:  
    double balance;  
};  
  
inline double Account::Deposit( double HowMuch )  
{  
    balance += HowMuch;  
    return balance;  
}  
  
int main()  
{  
}  
```  
  
> [!NOTE]
>  雖然成員函式可以在類別宣告內或分開定義，但是在類別定義之後，成員函式不可加入至該類別。  
  
 包含成員函式的類別可以具有多個宣告，不過成員函式本身在程式中只能有一個定義。  若有多個定義，則會在連結時產生錯誤訊息。  如果類別包含內嵌函式定義，則函式定義必須一致，以遵守這項「一個定義」的規則。  
  
## 請參閱  
 [成員函式](../misc/member-functions-cpp.md)