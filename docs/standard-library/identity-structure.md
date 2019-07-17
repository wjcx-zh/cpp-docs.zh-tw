---
title: identity 結構
ms.date: 11/04/2016
f1_keywords:
- utility/std::identity
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
ms.openlocfilehash: 49b2c1eb3ca03f9bf9199bdbca49348866ff0a7e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246157"
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

*左邊*\
要識別的值。

## <a name="remarks"></a>備註

此類別包含公用類型定義 `type`，這與範本參數 Type 相同。 它是與範本函式 [forward](../standard-library/utility-functions.md#forward) 搭配使用，以確保函式參數具有所需的類型。

為了與舊版程式碼相容，此類別亦定義識別函式`operator()`它會傳回其引數*左*。
