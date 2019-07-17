---
title: '&lt;執行&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 3bce34019f9ed4880d72a9d16c3c8b78dde0e0e3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268420"
---
# <a name="ltexecutiongt"></a>&lt;執行&gt;

描述平行演算法的執行原則。

## <a name="syntax"></a>語法

```
namespace std {
    template<class T> inline constexpr bool is_execution_policy_v = is_execution_policy<T>::value;
}
namespace std::execution {
    inline constexpr sequenced_policy seq { unspecified };
    inline constexpr parallel_policy par { unspecified };
    inline constexpr parallel_unsequenced_policy par_unseq { unspecified };
}
```
### <a name="classes-and-structs"></a>類別和結構

|||
|-|-|
|[is_execution_policy 結構](is-execution-policy-struct.md)|偵測到執行原則，以排除否則模稜兩可的多載解析參與的函式簽章。|
|[parallel_policy 類別](parallel-policy-class.md)|釐清平行演算法多載，並指出可能平行處理平行演算法的執行，以用做為唯一的類型。|
|[parallel_unsequenced_policy 類別](parallel-unsequenced-policy-class.md)|釐清平行演算法多載，並指出平行演算法的執行可能會平行處理和向量化，以用做為唯一的類型。|
|[sequenced_policy 類別](sequenced-policy-class.md)|釐清平行演算法多載，並要求可能不可以平行執行的平行演算法，以用做為唯一的類型。|

## <a name="requirements"></a>需求

**標頭：** \<執行 >

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[標頭檔參考](cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](cpp-standard-library-reference.md)
