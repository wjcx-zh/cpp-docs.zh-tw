---
title: auto_gcroot 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 48412a932ff3752b0613f7045cd88992332b7917
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423220"
---
# <a name="autogcroot-class"></a>auto_gcroot 類別

自動資源管理 (例如[auto_ptr 類別](../standard-library/auto-ptr-class.md)) 可用來將原生類型中嵌入虛擬控制代碼。

## <a name="syntax"></a>語法

```cpp
template<typename _element_type>
class auto_gcroot;
```

#### <a name="parameters"></a>參數

*_element_type*<br/>
要內嵌的 managed 的類型。

## <a name="requirements"></a>需求

**標頭檔** \<msclr\auto_gcroot.h >

**命名空間**msclr

## <a name="see-also"></a>另請參閱

[auto_gcroot](../dotnet/auto-gcroot.md)<br/>
[auto_gcroot 成員](../dotnet/auto-gcroot-members.md)<br/>
[如何：以原生類型宣告控制代碼](../dotnet/how-to-declare-handles-in-native-types.md)<br/>
[auto_handle 類別](../dotnet/auto-handle-class.md)