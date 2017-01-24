---
title: "__typeof | Microsoft Docs"
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
  - "__typeof_cpp"
  - "__typeof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof 關鍵字"
ms.assetid: d71b9603-35d0-4c62-b5b4-90ffc2305a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __typeof
**注意**：本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 請參閱 [typeid](../windows/typeid-cpp-component-extensions.md) 如需新語法中使用的相同功能。  
  
 傳回指定類型的 **System::Type**。  
  
```  
  
__typeof(  
typename  
)  
  
```  
  
 其中：  
  
 *typename*  
 您要命名為 **System::Type** 之 Managed 類型的名稱。 請注意，在 Managed 程式中，部分原生類型的別名是 Common Language Runtime 中的類型。 例如，`int` 是 **System::Int32** 的別名。  
  
## 備註  
 **\_\_typeof** 運算子可讓您取得您所指定之類型的 **System::Type** 類型。**\_\_typeof** 也可用於在自訂屬性區塊中傳回 **System::Type** 的值。 如需有關自行建立屬性的詳細資訊，請參閱[屬性](../windows/attribute.md)。  
  
## 範例  
 下列範例是將自訂屬性 \(`AtClass`\) 套用至 \_\_gc 類別 \(`B`\)。 然後再以 **\_\_typeof** 擷取自訂屬性的值：  
  
```  
// keyword__typeof.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __gc class MyClass {};  
  
[attribute(All)]  
__gc class AtClass {  
public:  
   AtClass(Type*) {  
      Console::WriteLine("in Type * constructor");  
   }  
  
   AtClass(String*) {}  
   AtClass(int) {}  
};  
  
[AtClass(__typeof(MyClass))]   // Apply AtClass attribute to class B  
__gc class B {};  
  
int main() {  
   Type * mytype = __typeof(B);  
   Object * myobject __gc[] = mytype -> GetCustomAttributes(true);  
   Console::WriteLine(myobject[0]);  
}  
```  
  
## 輸出  
  
```  
in Type * constructor  
AtClass  
```