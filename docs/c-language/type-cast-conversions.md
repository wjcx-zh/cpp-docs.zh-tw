---
title: 類型轉換 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data type conversion [C++], type-cast conversions
- conversions [C++], type-cast
- type casts
- explicit type conversions
- type casts [C++], about type-cast conversion
- type-cast conversions [C++]
ms.assetid: 57ab5902-f12f-4326-a2f6-6282f1d4025a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d040f3ce29f78b614c60d815cac16362374bddb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205606"
---
# <a name="type-cast-conversions"></a>類型轉換
您可以使用類型轉換明確地轉換類型。  
  
 **語法**  
  
 *cast-expression*：  
 *一元運算式*  
  
 **(**  *type-name*  **)**  *cast-expression*  
  
 *type-name*：  
 *specifier-qualifier-list abstract-declarator* opt  
  
 *type-name* 是一種類型，而 *cast-expression*是要轉換為該類型的值。 具有類型轉換的運算式不是左值。 *cast-expression* 會根據其指派給類型 *type-name* 的變數進行轉換。 指派的轉換規則 (於[指派轉換](../c-language/assignment-conversions.md)中說明) 也適用於類型轉換。 下表顯示可以轉換為任何指定類型的類型。  
  
### <a name="legal-type-casts"></a>合法的類型轉換  
  
|目的類型|潛在來源|  
|-----------------------|-----------------------|  
|整數類資料型別|任何整數類型或浮點類型，或物件的指標|  
|浮點|任何算術類型|  
|物件的指標，或 (**void** <strong>\*</strong>)|任何整數類型 (**void** <strong>\*</strong>)、物件的指標，或函式指標|  
|函式指標|任何整數類型、物件的指標，或函式指標|  
|結構、等位或陣列|無|  
|Void 類型|任何類型|  
  
 所有識別項都可以轉換成 `void` 類型。 不過，如果類型轉換運算式中指定的類型不是 `void`，則轉換成該類型的識別項不能是 `void` 運算式。 所有運算式都可以轉換成 `void`，但是類型 `void` 的運算式無法轉換成其他類型。 例如，具有 `void` 傳回類型的函式不能將其傳回值轉換成其他類型。  
  
 請注意，**void** <strong>\*</strong> 運算式具有 `void` 的類型指標，而不是類型 `void`。 如果某個物件轉換為 `void` 類型，則無法將產生的運算式指派給任何項目。 同樣地，類型轉換物件無法接受左值，因此無法對類型轉換物件進行指派。  
  
 **Microsoft 專屬**  
  
 只要識別項的大小不會變更，類型轉換可以是左值運算式。 如需左值運算式的詳細資訊，請參閱[左值和右值運算式](../c-language/l-value-and-r-value-expressions.md)。  
  
 **結束 Microsoft 專屬**  
  
 您可以使用轉換將運算式轉換成類型 `void`，但是產生的運算式只能在不需要值的位置使用。 轉換成 **void** <strong>\*</strong> 的物件指標，再轉換回原始類型將會返回其原始值。  
  
## <a name="see-also"></a>請參閱  
 [類型轉換](../c-language/type-conversions-c.md)