---
title: space_info 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::space_info
dev_langs:
- C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c0e9a636fea95a4ce829731c25605197ee00549
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206731"
---
# <a name="spaceinfo-structure"></a>space_info 結構

保留磁碟區的相關資訊。

## <a name="syntax"></a>語法

```cpp
struct space_info   {
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
    };
```

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|`unsigned long long available`|表示可用來代表磁碟區資料的位元組數目。|
|`unsigned long long capacity`|表示磁碟區可以表示的總位元組數目。|
|`unsigned long long free`|表示不用來代表磁碟區資料的位元組數目。|

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：** std::experimental::filesystem

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[space](https://msdn.microsoft.com/7fce0b0e-523b-4598-b218-47245d0204ca)<br/>
[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)<br/>
