---
title: "疑難排解例外狀況：System.IndexOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "IndexOutOfRangeException 類別"
ms.assetid: 9e28623c-93fc-4111-a0cb-c380e0b5de0c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IndexOutOfRangeException
嘗試存取陣列或集合的元素，而該陣列或集合中的索引位於陣列邊界外部或少於零時，就會擲回 <xref:System.IndexOutOfRangeException> 例外狀況。  
  
## 相關秘訣  
 **請確定清單索引的最大值必須小於清單的大小**  
 清單索引的最大值必須小於清單的大小。  
  
 **請確定索引不是負數。**  
 如果索引小於零，就會擲回這個例外狀況。  
  
 **請確定資料行名稱正確。**  
 如果提供給 <xref:System.Data.DataView.Sort%2A?displayProperty=fullName> 屬性的資料欄位名稱無效，可能會擲回這個例外狀況。 如需詳細資訊，請參閱 <xref:System.Data.DataView> 類別。  
  
## 範例  
  
### 描述  
 下列範例在索引 `Try…Catch` 超出陣列界限 0 至 3 時，使用 `IndexOutOfRangeException` 區塊來攔截 `i`。 範例會顯示下列資訊：  
  
 `Element at index 0: 3`  
  
 `Element at index 2: 5`  
  
 `Element at index -1: IndexOutOfRangeException caught`  
  
 `Element at index 4: IndexOutOfRangeException caught`  
  
### 程式碼  
  
```vb#  
Module Module1 Sub Main() ' The first two tests will display the value of the array element. IndexTest(0) IndexTest(2) ' The following two calls will display the information that ' an IndexOutOfRangeException was caught. IndexTest(-1) IndexTest(4) End Sub Sub IndexTest(ByVal i As Integer) Dim testArray() As Integer = {3, 4, 5, 6} Console.Write("Element at index {0}: ", i) Try Console.WriteLine(testArray(i)) Catch ex As IndexOutOfRangeException Console.WriteLine("IndexOutOfRangeException caught") End Try End Sub End Module  
```  
  
## 請參閱  
 <xref:System.IndexOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [陣列](../Topic/Arrays%20in%20Visual%20Basic.md)