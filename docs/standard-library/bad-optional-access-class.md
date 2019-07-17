---
title: bad_optional_access 類別
ms.date: 11/04/2016
f1_keywords:
- optional/std::bad_optional_access
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
ms.openlocfilehash: f898d1e30dd173339192bdb3b75581d12b62fca7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269140"
---
# <a name="badoptionalaccess-class"></a>bad_optional_access 類別

定義類型的物件擲回例外狀況，以嘗試對存取的值將情況回報為`optional`未包含值的物件。

## <a name="syntax"></a>語法

```cpp
class bad_optional_access : public exception
{
    public: bad_optional_access();
};
```
