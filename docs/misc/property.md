---
title: "__property | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__property_cpp"
  - "__property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__property 關鍵字"
  - "Managed 類別"
  - "屬性 [c + +]，受管理類別"
ms.assetid: 235e3574-6882-4c52-8301-270277b9216d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __property
> [!NOTE]
>  本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 請參閱 [property](../windows/property-cpp-component-extensions.md) 如需新語法中使用的相同功能。  
  
 宣告 Managed 類別的純量或索引屬性。  
  
## 語法  
  
```  
  
__property  
function-declarator  
  
```  
  
## 備註  
 `__property` 關鍵字引入了屬性宣告，而且可以出現在類別、介面或實值類型中。 屬性可以有 getter 函式 \(唯讀\)、setter 函式 \(唯寫\)，或兩者皆有 \(可讀寫\)。  
  
> [!NOTE]
>  屬性名稱不可與包含該屬性之 Managed 類別的名稱相符。 getter 函式的傳回類型必須符合對應 setter 函式之最後一個參數的類型。  
  
## 範例  
 下列範例會將純量屬性 \(`Size`\) 加入至 `MyClass` 宣告。 然後會使用 `get_Size` 和 `set_Size` 函式隱含設定及擷取這個屬性：  
  
```  
// keyword__property.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class MyClass {  
public:  
   MyClass() : m_size(0) {}  
   __property int get_Size() { return m_size; }  
   __property void set_Size(int value) { m_size = value; }  
   // compiler generates pseudo data member called Size  
protected:  
   int m_size;  
};  
  
int main() {  
   MyClass* class1 = new MyClass;  
   int curValue;  
  
   Console::WriteLine(class1->Size);  
  
   class1->Size = 4;   // calls the set_Size function with value==4  
   Console::WriteLine(class1->Size);  
  
   curValue = class1->Size;   // calls the get_Size function  
   Console::WriteLine(curValue);  
}  
```  
  
## 輸出  
  
```  
0  
4  
4  
```