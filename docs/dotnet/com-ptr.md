---
title: 'com:: ptr |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr
dev_langs:
- C++
helpviewer_keywords:
- com::ptr
ms.assetid: ee302e3c-8fed-4875-a372-2e55003718d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f5e6a3f7936e21d22282fe37a29b5d91f2e50caa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434488"
---
# <a name="comptr"></a>com::ptr

可當做 CLR 類別成員使用之 COM 物件的包裝函式。 包裝函式也會自動執行 COM 物件，呼叫其解構函式時，釋出已擁有的參考，在物件上的存留期管理。 類似於[CComPtr 類別](../atl/reference/ccomptr-class.md)。

## <a name="syntax"></a>語法

```
#include <msclr\com\ptr.h>
```

## <a name="remarks"></a>備註

[com:: ptr 類別](../dotnet/com-ptr-class.md)定義於\<msclr\com\ptr.h > 檔案。

## <a name="see-also"></a>另請參閱

[C++ 支援程式庫](../dotnet/cpp-support-library.md)