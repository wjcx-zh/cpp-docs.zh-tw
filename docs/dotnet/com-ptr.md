---
title: com::ptr
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr/com/com::ptr
helpviewer_keywords:
- com::ptr
ms.assetid: ee302e3c-8fed-4875-a372-2e55003718d3
ms.openlocfilehash: 993511142b72bd769fe8582b2650e5d020bd6ce2
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446262"
---
# <a name="comptr"></a>com::ptr

可當做 CLR 類別成員使用之 COM 物件的包裝函式。 包裝函式也會自動執行 COM 物件的存留期管理，並在呼叫其析構器時釋放物件上擁有的參考。 類似于[CComPtr 類別](../atl/reference/ccomptr-class.md)。

## <a name="syntax"></a>語法

```
#include <msclr\com\ptr.h>
```

## <a name="remarks"></a>備註

[com：:p Tr 類別](../dotnet/com-ptr-class.md)是在 \<msclr\com\ptr.h > 檔中定義。

## <a name="see-also"></a>另請參閱

[C++ 支援程式庫](../dotnet/cpp-support-library.md)
