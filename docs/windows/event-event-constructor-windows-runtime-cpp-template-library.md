---
title: 'Event:: event 建構函式 （Windows 執行階段 c + + 樣板程式庫） |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
dev_langs:
- C++
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bd9f02935d0d88976fd3b62c7276f106519fa74
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381006"
---
# <a name="eventevent-constructor-windows-runtime-c-template-library"></a>Event::Event 建構函式 (Windows 執行階段 C++ 樣板程式庫)

初始化的新執行個體**事件**類別。

## <a name="syntax"></a>語法

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
事件的控制代碼。 根據預設， *h*初始化為**nullptr**。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Event 類別 (Windows 執行階段 C++ 範本庫)](../windows/event-class-windows-runtime-cpp-template-library.md)