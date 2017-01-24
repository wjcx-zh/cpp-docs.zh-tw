---
title: "__box | Microsoft Docs"
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
  - "__box"
  - "__box_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__box 關鍵字"
  - "Boxing"
  - "unboxing"
  - "boxing，__box 關鍵字"
ms.assetid: 935b4a4d-fc45-484c-87c6-d95cfc67cc9d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __box
> [!NOTE]
>  本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 請參閱 [Boxing](../windows/boxing-cpp-component-extensions.md) 如需新語法中使用的相同功能。  
  
 建立 \_\_value 類別物件的 Managed 複本。  
  
## 語法  
  
```  
  
__box(  
value-class identifier  
)  
  
```  
  
## 備註  
 `__box` 關鍵字可用來從現有的 \_\_value 類別物件建立 Managed 物件 \(衍生自 **System::ValueType**\)。 當 `__box` 關鍵字套用至 \_\_value 類別時：  
  
-   Managed 物件會配置在 Common Language Runtime 堆積上。  
  
-   \_\_value 類別物件的目前值會以位元為單位複製到 Managed 物件中。  
  
-   將會傳回新 Managed 物件的位址。  
  
 這個程序稱為 Boxing。 這樣一來，所有 \_\_value 類別物件就能在適用於任何 Managed 物件的泛型常式中使用，因為 Managed 物件會從 **System::Object** 間接繼承 \(因為 **System::ValueType** 是從 **System::Object** 繼承\)。  
  
> [!NOTE]
>  新建立的 Boxed 物件是 \_\_value 類別物件的複本。 因此，對 Boxed 物件值的修改不會影響 \_\_value 類別物件的內容。  
  
## 範例  
 以下是進行 Boxing 和 Unboxing 的範例：  
  
```  
// keyword__box.cpp  
// compile with: /clr:oldSyntax  
#using < mscorlib.dll >  
using namespace System;  
  
int main() {  
  Int32 i = 1;  
  System::Object* obj = __box(i);  
  Int32 j = *dynamic_cast<__box Int32*>(obj);  
}  
```  
  
 在下列範例中，Unmanaged 實值類型 \(`V`\) 會進行 Boxed 並且做為 Managed 參數傳遞至 `Positive` 函式。  
  
```  
// keyword__box2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__value struct V {  
   int i;  
};  
void Positive(Object*) {}   // expects a managed class  
  
int main() {  
   V v={10};   // allocate and initialize  
   Console::WriteLine(v.i);  
  
   // copy to the common language runtime heap  
   __box V* pBoxedV = __box(v);  
   Positive(pBoxedV);   // treat as a managed class  
  
   pBoxedV->i = 20;   // update the boxed version  
   Console::WriteLine(pBoxedV->i);  
}  
```  
  
 **10 20**