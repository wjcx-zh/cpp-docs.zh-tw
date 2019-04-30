---
title: space_info 結構
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::space_info
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
ms.openlocfilehash: b6998f4ac7ced2d85063186edbd47227b6d24ca5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399443"
---
# <a name="spaceinfo-structure"></a>space_info 結構

保留磁碟區的相關資訊。

## <a name="syntax"></a>語法

```cpp
struct space_info
{
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
};
```

## <a name="members"></a>成員

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|`unsigned long long capacity`|表示磁碟區可以表示的總位元組數目。|
|`unsigned long long free`|表示不用來代表磁碟區資料的位元組數目。|
|`unsigned long long available`|表示可用來代表磁碟區資料的位元組數目。|

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：** std::experimental::filesystem

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[檔案系統巡覽 (C++)](../standard-library/file-system-navigation.md)<br/>
