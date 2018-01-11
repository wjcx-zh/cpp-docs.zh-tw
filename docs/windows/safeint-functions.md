---
title: "SafeInt 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: functions, SafeInt
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
caps.latest.revision: "13"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ae482b7f58d64a46b82b32c6c6d62d7f69f0dce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="safeint-functions"></a>SafeInt 函式
SafeInt 程式庫提供幾個函式，您可以使用而建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。 如果您想要保護單一數學作業從整數的溢位時，您可以使用這些函式。 如果您想要保護多個數學作業時，您應該建立`SafeInt`物件。 若要建立更有效率`SafeInt`比使用這些函式數次的物件。  
  
 這些功能可讓您比較，或執行而不需要先將它們轉換成相同類型的兩個不同類型的參數上的數學運算。  
  
 這些函式各有兩個範本類型：`T`和`U`。 每個類型可以是布林值、 字元或整數類資料類型。 可以帶正負號或不帶正負號整數類資料類型和任何從 8 位元到 64 位元的大小。  
  
## <a name="in-this-section"></a>本節內容  
  
|功能|描述|  
|--------------|-----------------|  
|[SafeAdd](../windows/safeadd.md)|兩個數字相加，並防止溢位。|  
|[SafeCast](../windows/safecast.md)|會轉換成另一個類型參數的一種。|  
|[SafeDivide](../windows/safedivide.md)|兩數相除並防止除以零。|  
|[SafeEquals](../windows/safeequals.md)， [SafeGreaterThan](../windows/safegreaterthan.md)， [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)， [SafeLessThan](../windows/safelessthan.md)， [SafeLessThanEquals](../windows/safelessthanequals.md)，[SafeNotEquals](../windows/safenotequals.md)|比較兩個數字。 這些功能可讓您比較兩個不同類型的數字，而不需要變更其類型。|  
|[SafeModulus](../windows/safemodulus.md)|執行兩個數字的模數作業。|  
|[SafeMultiply](../windows/safemultiply.md)|在一起的兩個數目相乘，並防止溢位。|  
|[SafeSubtract](../windows/safesubtract.md)|兩個數字相減，可防止溢位。|  
  
## <a name="related-sections"></a>相關章節  
  
|區段|描述|  
|-------------|-----------------|  
|[SafeInt 類別](../windows/safeint-class.md)|`SafeInt` 類別。|  
|[SafeIntException 類別](../windows/safeintexception-class.md)|SafeInt 程式庫的特定例外狀況類別。|