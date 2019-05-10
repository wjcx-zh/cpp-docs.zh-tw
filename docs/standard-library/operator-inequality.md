---
title: operator!=
ms.date: 11/04/2016
f1_keywords:
- std::!=
- '!='
- std::operator!=
- std.operator!=
- std.!=
- operator!=
helpviewer_keywords:
- '!= operator'
- operator!=
- operator !=
ms.assetid: ef2be7f0-1c94-4edc-b65c-731fddd519f4
ms.openlocfilehash: e29088b64b46e3aa907f4a09ec131c6f9b68a74b
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220509"
---
# <a name="operator"></a>operator!=

> [!NOTE]
> 本主題位於 MicrosoftC++中所用容器的無作用範例文件C++標準程式庫。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

多載 `operator!=` 來比較樣板類別 [Container](../standard-library/sample-container-class.md) 的兩個物件。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
bool operator!=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>傳回值

傳回 `!(left == right)`。

## <a name="see-also"></a>另請參閱

[\<範例容器>](../standard-library/sample-container.md)<br/>
