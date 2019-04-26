---
title: raw_native_types
ms.date: 11/04/2016
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: 32b77905ef7025334e5101e76864da9a15c50cf6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180475"
---
# <a name="rawnativetypes"></a>raw_native_types
**C++特定**

停用在高階包裝函式中使用 COM 支援類別，並強制改用低階資料類型。

## <a name="syntax"></a>語法

```
raw_native_types
```

## <a name="remarks"></a>備註

根據預設，高階錯誤處理方法會使用 COM 支援類別[_bstr_t](../cpp/bstr-t-class.md)並[_variant_t](../cpp/variant-t-class.md)取代`BSTR`和`VARIANT`資料類型與原始 COM 介面指標。 這些類別會封裝為這些資料類型配置和解除配置之記憶體儲存區的詳細資料，並且大幅簡化類型轉換和轉換作業。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)