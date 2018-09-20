---
title: 'Synclockwithstatust:: Synclockwithstatust 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 020632ff17ade10e7fcb9cd46d245849189b6860
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416782"
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT 建構函式

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>參數

*other*<br/>
右值參考到另一個**SyncLockWithStatusT**物件。

*sync*<br/>
另一個的參考**SyncLockWithStatusT**物件。

*status*<br/>
值[status_](../windows/synclockwithstatust-status-data-member.md)資料成員*其他*參數或*同步*參數。

## <a name="remarks"></a>備註

初始化的新執行個體**SyncLockWithStatusT**類別。

第一個建構函式初始化目前**SyncLockWithStatusT**物件從另一個**SyncLockWithStatusT**參數所指定*其他*，然後失效另**SyncLockWithStatusT**物件。 第二個建構函式**保護**，並初始化目前**SyncLockWithStatusT**為無效狀態的物件。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>另請參閱

[SyncLockWithStatusT 類別](../windows/synclockwithstatust-class.md)<br/>
[SyncLockWithStatusT::GetStatus 方法](../windows/synclockwithstatust-getstatus-method.md)