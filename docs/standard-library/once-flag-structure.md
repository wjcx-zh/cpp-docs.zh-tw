---
title: once_flag 結構 | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67cfbe06461598fbd04e124629399baa63fdd5d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104331"
---
# <a name="onceflag-structure"></a>once_flag 結構

代表**struct**搭配範本函式[call_once](../standard-library/mutex-functions.md#call_once)以確保該初始化程式碼會呼叫一次，即使執行多個執行緒。

## <a name="syntax"></a>語法

結構 once_flag {constexpr once_flag() noexcept;};

## <a name="remarks"></a>備註

`once_flag` **Struct**只有預設建構函式。

可以建立 `once_flag` 類型的物件，但無法複製它們。

## <a name="requirements"></a>需求

**標頭：** \<mutex >

**命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
