---
title: no_smart_pointers 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- no_smart_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 1fca3eb486ff3cfc7403c38e91855b799a698782
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220696"
---
# <a name="no_smart_pointers-import-attribute"></a>no_smart_pointers 匯入屬性

**C++特殊**

不為類型程式庫中的所有介面建立智慧型指標。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***no_smart_pointers**

## <a name="remarks"></a>備註

根據預設，當您使用 `#import` 時，會得到類型程式庫中所有介面的智慧型指標宣告。 這些智慧型指標的類型是[_com_ptr_t](../cpp/com-ptr-t-class.md)。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
