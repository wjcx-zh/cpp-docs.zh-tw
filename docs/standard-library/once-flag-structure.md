---
title: once_flag 結構
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: fb85bd48f9b1ac10ec2fefbc6738aae777f67bcf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455199"
---
# <a name="onceflag-structure"></a>once_flag 結構

表示與樣板函式[call_once](../standard-library/mutex-functions.md#call_once)搭配使用的**結構**, 以確保初始化程式碼只會呼叫一次, 即使有多個執行緒執行也一樣。

## <a name="syntax"></a>語法

struct once_flag { constexpr once_flag() noexcept; };

## <a name="remarks"></a>備註

結構只有預設的函式。  `once_flag`

可以建立 `once_flag` 類型的物件，但無法複製它們。

## <a name="requirements"></a>需求

**標頭:** \<mutex >

**命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
