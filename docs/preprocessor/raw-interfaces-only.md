---
title: raw_interfaces_only 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 4b79aa4dbafa204d84f4d6ed7ec78fdec1b81fa7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216215"
---
# <a name="raw_interfaces_only-import-attribute"></a>raw_interfaces_only 匯入屬性

**C++特殊**

抑制產生錯誤處理包裝函式, 以及使用這些包裝函數的[屬性](../cpp/property-cpp.md)宣告。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***raw_interfaces_only**

## <a name="remarks"></a>備註

**Raw_interfaces_only**屬性也會導致用來命名非屬性函式的預設前置詞會被移除。 一般來說, 前置詞為`raw_`。 如果指定這個屬性, 則會直接從類型程式庫取得函式名稱。

這個屬性只能讓您公開類型程式庫中的低階內容。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
