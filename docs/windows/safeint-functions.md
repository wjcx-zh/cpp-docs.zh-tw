---
title: "SafeInt 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式, SafeInt"
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
caps.latest.revision: 13
caps.handback.revision: 13
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeInt 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

SafeInt 程式庫提供您使用，而不建立 [SafeInt 類別](../windows/safeint-class.md)的執行個體數的函式。  如果您想要保護單一數學運算免於整數溢位，您可以使用這些函式。  如果您想要保護多個數學運算，您應該建立 `SafeInt` 物件。  更有效率的方法建立 `SafeInt` 物件要比使用這些函式多次。  
  
 這些函式可讓您比較或執行參數的兩種不同類型的算術運算，而不需要先將它們轉換成相同型別。  
  
 這些函式都具有兩個範本類型: `T` 和 `U`。  這些型別都可以是布林值、字元或整數型別。  整數類資料型別可以是帶正負號或不帶正負號和從 8 位元的任何大小為 64 位元。  
  
## 在本節中  
  
|功能|說明|  
|--------|--------|  
|[SafeAdd](../windows/safeadd.md)|將兩個數字相加並防止溢位。|  
|[SafeCast](../windows/safecast.md)|轉換參數的型別為另一種型別。|  
|[SafeDivide](../windows/safedivide.md)|兩數相除並避免除以零。|  
|[SafeEquals](../windows/safeequals.md), [SafeGreaterThan](../windows/safegreaterthan.md), [SafeGreaterThanEquals](../windows/safegreaterthanequals.md), [SafeLessThan](../windows/safelessthan.md), [SafeLessThanEquals](../windows/safelessthanequals.md), [SafeNotEquals](../windows/safenotequals.md)|比較兩個數字。  這些函式可讓您比較數值的兩種不同類型，而不需要變更它們的型別。|  
|[SafeModulus](../windows/safemodulus.md)|執行兩個數字的模數運算。|  
|[SafeMultiply](../windows/safemultiply.md)|乘以一起兩數相除防止溢位。|  
|[SafeSubtract](../windows/safesubtract.md)|減去兩個數字並防止溢位。|  
  
## 相關章節  
  
|區段|說明|  
|--------|--------|  
|[SafeInt 類別](../windows/safeint-class.md)|`SafeInt` 類別。|  
|[SafeIntException 類別](../windows/safeintexception-class.md)|對 SafeInt 程式庫的例外狀況類別特定的。|