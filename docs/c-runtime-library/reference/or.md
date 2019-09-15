---
title: 或
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- std::or
- std.or
- Or
helpviewer_keywords:
- or function
ms.assetid: 6523b3ac-0a18-44ec-9e9a-b9bab8525ead
ms.openlocfilehash: 5d1d36f3147b746602be03b21867cefde2e32495
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951065"
---
# <a name="or"></a>或

&#124;&#124; 運算子的替代項目。

## <a name="syntax"></a>語法

```C

#define or ||
```

## <a name="remarks"></a>備註

巨集會產生 &#124;&#124; 運算子。

## <a name="example"></a>範例

```cpp
// iso646_or.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   bool a = true, b = false, result;

   boolalpha(cout);

   result= a || b;
   cout << result << endl;

   result= a or b;
   cout << result << endl;
}
```

```Output
true
true
```

## <a name="requirements"></a>需求

**標頭：** \<iso646.h>