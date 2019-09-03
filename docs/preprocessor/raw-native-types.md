---
title: raw_native_types 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: eb08a8e7cb081bd7a470c3c1ecf1492a7a65f833
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216065"
---
# <a name="raw_native_types-import-attribute"></a>raw_native_types 匯入屬性

**C++特殊**

停用在高階包裝函式中使用 COM 支援類別, 並改為強制使用低層級的資料類型。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***raw_native_types**

## <a name="remarks"></a>備註

根據預設, 高階錯誤處理方法會使用 COM 支援類別[_bstr_t](../cpp/bstr-t-class.md)和[_variant_t](../cpp/variant-t-class.md)來`BSTR`取代和`VARIANT`資料類型和原始的 COM 介面指標。 這些類別會封裝為這些資料類型配置和解除配置之記憶體儲存區的詳細資料，並且大幅簡化類型轉換和轉換作業。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
