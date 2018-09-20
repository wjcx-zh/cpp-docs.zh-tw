---
title: auto_handle 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- auto_handle, msclr::auto_handle
- msclr.auto_handle
dev_langs:
- C++
helpviewer_keywords:
- auto_handle class
ms.assetid: a65604d1-ecbb-44fd-ae2f-696ddeeed9d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6509eaf8797d20303100c9886590bb2971e6c640
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419148"
---
# <a name="autohandle-class"></a>auto_handle 類別

自動資源管理可將 managed 類型中嵌入虛擬控制代碼。

## <a name="syntax"></a>語法

```
template<typename _element_type>
ref class auto_handle;
```

#### <a name="parameters"></a>參數

*_element_type*<br/>
要內嵌的 managed 的類型。

## <a name="requirements"></a>需求

**標頭檔** \<msclr\auto_handle.h >

**命名空間**msclr

## <a name="see-also"></a>另請參閱

[auto_handle](../dotnet/auto-handle.md)<br/>
[auto_handle 成員](../dotnet/auto-handle-members.md)<br/>
[auto_gcroot 類別](../dotnet/auto-gcroot-class.md)