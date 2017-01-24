---
title: "這個版本不支援屬性 &#39;System.Runtime.InteropServices.DefaultCharSetAttribute&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32510"
  - "vbc32510"
helpviewer_keywords: 
  - "BC32510"
ms.assetid: e2eec233-6e0b-4f2f-a801-b0274e579c0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 這個版本不支援屬性 &#39;System.Runtime.InteropServices.DefaultCharSetAttribute&#39;
<xref:System.Runtime.InteropServices.DefaultCharSetAttribute?displayProperty=fullName> 屬性可讓您指定要用於封送處理字串的字元集。 它的值會採用 <xref:System.Runtime.InteropServices.CharSet?displayProperty=fullName> 列舉的成員。  
  
 目前的 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 版本不支援這個屬性。 可能會在未來版本中進行支援。  
  
 **錯誤 ID︰**BC32510  
  
### 更正這個錯誤  
  
-   使用每個 [Declare Statement](../Topic/Declare%20Statement.md) 來指定所宣告外部程序的字元集。 下列範例將說明這點。  
  
    ```  
    Ansi Declare Function GetUserName Lib "advapi32.dll" _ (ByVal lpBuffer As String, ByRef nSize As Integer) As Integer Unicode Declare Sub externalProc Lib "projectlib.dll" _ (ByVal arg As Double)  
    ```  
  
     如果您未在 `Declare` 陳述式中指定字元集，則會預設為 ANSI。  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute>   
 <xref:System.Runtime.InteropServices.CharSet>   
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Declare Statement](../Topic/Declare%20Statement.md)