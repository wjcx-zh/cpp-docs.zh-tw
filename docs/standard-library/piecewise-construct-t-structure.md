---
title: piecewise_contruct_t 結構
ms.date: 11/04/2016
f1_keywords:
- utility/std::piecewise_contruct_t
helpviewer_keywords:
- piecewise_contruct_t class
- piecewise_contruct_t structure
ms.openlocfilehash: 6a9a6af97ca5c7751d64cd1fa70c9d9eba87da7c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268360"
---
# <a name="piecewisecontructt-structure"></a>piecewise_contruct_t 結構

結構`piecewise_construct_t`是空的結構類型用來保存不同的建構函式和函式多載。 具體而言，`pair`使用的建構函式`piecewise_construct_t`做為第一個引數，後面加上兩個`tuple`引數。

## <a name="syntax"></a>語法

```cpp
struct piecewise_construct_t { explicit piecewise_construct_t() = default; };

inline constexpr piecewise_construct_t piecewise_construct{};
```
