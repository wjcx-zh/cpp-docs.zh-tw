---
title: bad_any_cast 類別
ms.date: 04/04/2019
f1_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
helpviewer_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
ms.openlocfilehash: b47ca4f615c6f317f17ce64e8388ae5d698185ea
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844583"
---
# <a name="bad_any_cast-class"></a>bad_any_cast 類別

失敗的擲回物件 `any_cast` 。

## <a name="syntax"></a>語法

```cpp
class bad_any_cast
```

### <a name="member-functions"></a>成員函數

|名稱|描述|
|-|-|
|[哪些](#what)|傳回類型。|

## <a name="what"></a><a name="what"></a> 哪些

傳回類型。

```cpp
const char* what() const noexcept override;
```
