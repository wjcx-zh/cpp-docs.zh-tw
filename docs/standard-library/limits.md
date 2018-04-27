---
title: '&lt;limits&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- limits/std::<limits>
- <limits>
dev_langs:
- C++
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84437f53d8685c842e102fac3da7b062058bb20e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

定義範本類別 `numeric_limits` 和兩個關於浮點表示法和捨入的列舉。

## <a name="syntax"></a>語法

```cpp
#include <limits>

```

## <a name="remarks"></a>備註

`numeric_limits` 類別的明確特製化可說明基本類型的許多屬性，包括字元、整數和浮點類型，以及由實作所定義，而非由 C++ 語言的規則所修正的 `bool`。 \<limits> 中所描述的屬性包括精確度、最小和最大表示法、捨入和訊號類型錯誤。

### <a name="enumerations"></a>列舉

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|此列舉會說明實作可選擇用來代表反正規化浮點值的各種方法 (反正規化浮點值是指太小而無法表示為正規化值的值)：|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|此列舉會說明實作可選擇用來將浮點值捨入為整數值的各種方法。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[numeric_limits 類別](../standard-library/numeric-limits-class.md)|此範本類別可說明內建數值類型的算術屬性。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
