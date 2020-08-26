---
title: '&lt;執行&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: f37458fdc0b58968e095a7c59de797eac295bde7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835932"
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

|名稱|描述|
|-|-|
|[is_execution_policy 結構](is-execution-policy-struct.md)|偵測到執行原則的目的是要排除函式簽章，否則不明確的多載解析參與。|
|[parallel_policy 類別](parallel-policy-class.md)|當做獨特型別使用，以區分平行演算法多載，並指出平行演算法的執行可能會平行處理。|
|[parallel_unsequenced_policy 類別](parallel-unsequenced-policy-class.md)|當做獨特型別使用，以區分平行演算法多載，並指出平行演算法的執行可能會平行處理和向量化。|
|[sequenced_policy 類別](sequenced-policy-class.md)|當做獨特型別使用，以區分平行演算法多載，並要求平行演算法的執行不會進行平行處理。|

## <a name="requirements"></a>規格需求

**標頭：**\<execution>

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[標頭檔參考](cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](cpp-standard-library-reference.md)
