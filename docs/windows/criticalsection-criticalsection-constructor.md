---
title: 'Criticalsection:: Criticalsection 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 892a32c6ff6f8e9a3a30452d05dd6e15c38a4fa8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605048"
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection 建構函式

初始化同步處理物件，類似於 mutex 物件，但可由單一的程序的執行緒。

## <a name="syntax"></a>語法

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>參數

*spincount*  
重要區段物件旋轉計數。 預設值為 0。

## <a name="remarks"></a>備註

如需關鍵區段和 spincounts 的詳細資訊，請參閱`InitializeCriticalSectionAndSpinCount`函式中**同步處理**Windows API 文件的區段。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[CriticalSection 類別](../windows/criticalsection-class.md)