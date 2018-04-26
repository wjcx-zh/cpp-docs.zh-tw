---
title: '&lt;bitset&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <bitset>
dev_langs:
- C++
helpviewer_keywords:
- <bitset> header
- bitset header
ms.assetid: af30a9b9-489e-46e3-9d29-5f3ea07ae6dc
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71b2f2d8c12c2d82b1e2a2ba2c68f061ce518658
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ltbitsetgt"></a>&lt;bitset&gt;

定義樣板類別位元集，以及兩個代表和操作固定大小位元序列的支援樣板函式。

## <a name="syntax"></a>語法

```

#include <bitset>

```

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator&](../standard-library/bitset-operators.md#op_amp)|在兩個位元集之間執行位元 AND。|
|[operator<\<](../standard-library/bitset-operators.md#op_lt_lt)|將位元序列的文字表示插入標準輸出資料流。|
|[operator>>](../standard-library/bitset-operators.md#op_gt_gt)|將位元序列的文字表示插入標準輸入資料流。|
|[operator^](../standard-library/bitset-operators.md#op_xor)|在兩個位元集之間執行位元 EXCLUSIVE-OR。|
|[operator&#124;](../standard-library/bitset-operators.md#op_or)|在兩個位元集之間執行位元 OR。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[bitset 類別](../standard-library/bitset-class.md)|這個樣板類別所描述的物件類型，可儲存由固定位元數所組成的序列，以提供精簡的方式，來保留一組項目或條件的旗標。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
