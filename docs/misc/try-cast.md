---
title: "__try_cast | Microsoft Docs"
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
  - "__try_cast"
  - "__try_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__try_cast 關鍵字"
  - "轉型失敗"
  - "例外狀況，不成功的轉型"
  - "擲回例外狀況，不成功的轉型"
ms.assetid: e9e5da3a-f5b9-4915-b30a-a432e8574d03
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __try_cast
**注意**：本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 請參閱 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md) 如需新語法中使用的相同功能。  
  
 如果轉型失敗，會執行指定的轉型或擲回例外狀況。  
  
## 語法  
  
```  
  
__try_cast <  
 type-id  
 >  
(  
expression   
)  
  
```  
  
## 備註  
 `__try_cast` 關鍵字 \(與 [dynamic\_cast](../cpp/dynamic-cast-operator.md) 的行為類似\) 支援在指定的轉型作業失敗時自動擲回例外狀況 \(屬於類型 **System::InvalidCastException**\)。  
  
 應用程式測試階段可以使用 `__try_cast` 關鍵字自動提醒您注意可能發生的轉型失敗。  
  
 當移植 Managed Extensions for c \+ \+，來取代 `__try_cast` 呼叫 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)。  
  
 因為在執行階段無法檢查類型，因此 `__try_cast` 在將指標轉型為實值類型 \([\_\_value](../misc/value.md)\) 時無法發揮作用。  
  
## 範例  
 下列範例會嘗試將指標 \(類型為 `Derived`\) 轉型為另一個指標 \(類型為 `MoreDerived`\)。 如果轉型失敗，catch 區塊會進行攔截並報告：  
  
```  
// keyword__try_cast.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc struct Base {};   
__gc struct Derived : Base {};  
__gc struct MoreDerived : Derived {};  
  
int main() {  
   Base*bp = new Derived;  
   try {  
       MoreDerived* mdp = __try_cast<MoreDerived*>(bp);  
   }  
   catch(System::InvalidCastException*) {  
       Console::WriteLine("Could not cast 'bp' to MoreDerived*");  
   }  
}  
```  
  
## 輸出  
  
```  
Could not cast 'bp' to MoreDerived*  
```