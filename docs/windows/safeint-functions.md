---
title: SafeInt 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions, SafeInt
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b8a0475b5d3ba9053cd5d2df5ffd99ce9292ba8e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603451"
---
# <a name="safeint-functions"></a>SafeInt 函式
SafeInt 程式庫提供數個您可以使用而建立的執行個體的函數[SafeInt 類別](../windows/safeint-class.md)。 如果您想要保護單一數學作業從整數的溢位時，您可以使用這些函式。 如果您想要保護多個數學運算，您應該建立**SafeInt**物件。 若要建立更有效率**SafeInt**比使用這些函式多次的物件。  
  
 這些功能可讓您比較，或執行而不需要先將它們轉換成相同類型的兩個不同類型的參數上的數學運算。  
  
 所有這些函式有兩種範本類型：`T`和`U`。 每一種類型可以是布林值、 字元或整數類資料類型。 可以帶正負號或不帶正負號整數類資料類型及任何大小從 8 位元到 64 位元。  
  
## <a name="in-this-section"></a>本節內容  
  
|功能|描述|  
|--------------|-----------------|  
|[SafeAdd](../windows/safeadd.md)|兩個數字相加，並防止溢位。|  
|[SafeCast](../windows/safecast.md)|將轉換成另一個類型參數的一種。|  
|[SafeDivide](../windows/safedivide.md)|兩數相除並防止除以零。|  
|[SafeEquals](../windows/safeequals.md)， [SafeGreaterThan](../windows/safegreaterthan.md)， [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)， [SafeLessThan](../windows/safelessthan.md)， [SafeLessThanEquals](../windows/safelessthanequals.md)， [SafeNotEquals](../windows/safenotequals.md)|比較兩個數字。 這些功能可讓您比較兩種不同的數字，而不需要變更其類型。|  
|[SafeModulus](../windows/safemodulus.md)|執行模數作業上兩個數字。|  
|[SafeMultiply](../windows/safemultiply.md)|在一起的兩個數目相乘，並防止溢位。|  
|[SafeSubtract](../windows/safesubtract.md)|兩個數字相減，並防止溢位。|  
  
## <a name="related-sections"></a>相關章節  
  
|區段|描述|  
|-------------|-----------------|  
|[SafeInt 類別](../windows/safeint-class.md)|**SafeInt**類別。|  
|[SafeIntException 類別](../windows/safeintexception-class.md)|SafeInt 程式庫的特定例外狀況類別。|