---
title: identity 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- utility/std::identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83180020c20f78c16af0b1b33bada91936b6af9b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="identity-structure"></a>identity 結構

一種提供類型定義來作為範本參數的結構。

## <a name="syntax"></a>語法

```cpp
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };
```
### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`left`|要識別的值。|

## <a name="remarks"></a>備註

此類別包含公用類型定義 `type`，這與範本參數 Type 相同。 它是與範本函式 [forward](../standard-library/utility-functions.md#forward) 搭配使用，以確保函式參數具有所需的類型。

為了與舊版程式碼相容，此類別也會定義識別函式 `operator()`，此函式會傳回其引數 `left`。

## <a name="requirements"></a>需求

**標頭：**\<utility>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<utility>](../standard-library/utility.md)<br/>
