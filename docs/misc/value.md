---
title: "__value | Microsoft Docs"
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
  - "__value_cpp"
  - "__value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__value 關鍵字"
  - "實值型別宣告"
  - "__value 關鍵字語法"
ms.assetid: b14b64f7-5db6-4e92-a144-fcbf67572b49
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __value
> [!NOTE]
>  本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 請參閱 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md) 如需新語法中使用的相同功能。  
  
 將類別宣告為 \_\_value 類型。  
  
## 語法  
  
```  
  
__value  
 class-specifier  
__value  
 struct-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
  
```  
  
## 備註  
 `__value` 類型與 `__gc` 類型的不同之處在於，`__value` 類型變數直接包含其資料，而 Managed 變數會指向其儲存在 Common Language Runtime 堆積上的資料。  
  
 下列條件適用於 `__value` 類型：  
  
-   `__value` 關鍵字無法套用至介面。  
  
-   `__value` 類型可以從任意數目的介面繼承，但是無法從其他類型或 `__value` 類型繼承。  
  
-   `__value` 類型是根據定義密封。 如需詳細資訊，請參閱 [\_\_sealed](../misc/sealed.md)。  
  
-   在任何可以使用 Managed 類型的位置都可以使用 `__value` 類型。  
  
> [!NOTE]
>  不允許使用 `__value` 關鍵字搭配 `__abstract` 關鍵字。  
  
 `__value` 類型可以明確連接至 **System::Object** 指標。 這稱為 Boxing。  
  
 下列方針適用於在 `__nogc` 類型內部內嵌實值類型：  
  
-   實值類型必須有 **LayoutSequential** 或 **LayoutExplicit**。  
  
-   實值類型不能有 gc 指標成員。  
  
-   實值類型不能有 private 資料成員。  
  
 在 Managed Extensions for C\+\+ 中，C\# 類別和 C\# 結構的對等用法如下：  
  
|Managed Extensions for C\+\+|C\#|如需詳細資訊|  
|----------------------------------|---------|------------|  
|\_\_gc 結構<br /><br /> \-或\-<br /><br /> \_\_gc 類別|Class \- 類別|[class](../Topic/class%20\(C%23%20Reference\).md) 關鍵字|  
|\_\_value 結構<br /><br /> \-或\-<br /><br /> \_\_value 類別|struct|[struct](../Topic/struct%20\(C%23%20Reference\).md) 關鍵字|  
  
## 範例  
 下列範例會宣告 `__value` 類型 \(`V`\)，然後管理兩個 `__value` 類型的執行個體：  
  
```  
// keyword__value.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value struct V {   
   int m_i;  
};  
  
int main() {  
   V v1, v2;  
   v1.m_i = 5;  
   v2 = v1;   // copies all fields of v1 to v2  
   v2.m_i = 6;   // does not affect v1.m_I  
}  
```