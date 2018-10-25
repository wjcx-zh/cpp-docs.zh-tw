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
ms.openlocfilehash: 62acade082847386e065470f23ffe8374f82eb55
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079190"
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
|*left*|要識別的值。|

## <a name="remarks"></a>備註

此類別包含公用類型定義 `type`，這與範本參數 Type 相同。 它是與範本函式 [forward](../standard-library/utility-functions.md#forward) 搭配使用，以確保函式參數具有所需的類型。

為了與舊版程式碼相容，此類別亦定義識別函式`operator()`它會傳回其引數*左*。

## <a name="requirements"></a>需求

**標頭：**\<utility>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<utility>](../standard-library/utility.md)<br/>
