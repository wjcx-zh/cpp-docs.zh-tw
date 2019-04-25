---
title: Platform::CallbackContext 列舉
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 7f4e020ab0b1e377456c27d3b4666e15b5a4f7a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161662"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext 列舉

指定回呼函式 (事件處理常式) 會執行的執行緒內容。

## <a name="syntax"></a>語法

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>成員

|類型程式碼|描述|
|---------------|-----------------|
|任何|回呼函式可以在任何執行緒的內容中執行。|
|相同|回呼函式只能在啟動非同步作業的執行緒內容中執行。|

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd