---
title: once_flag 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 4275b99ada0dbfe1c974446d21862f7fa73aab38
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964492"
---
# <a name="onceflag-structure"></a>once_flag 結構

代表**struct**搭配範本函式[call_once](../standard-library/mutex-functions.md#call_once)以確保該初始化程式碼會呼叫一次，即使執行多個執行緒。

## <a name="syntax"></a>語法

struct once_flag { constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag& operator=(const once_flag&); };

## <a name="remarks"></a>備註

`once_flag` **Struct**只有預設建構函式。

可以建立 `once_flag` 類型的物件，但無法複製它們。

## <a name="requirements"></a>需求

**標頭：** \<mutex >

**命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
