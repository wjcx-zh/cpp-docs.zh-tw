---
title: no_dual_interfaces 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: 6270888f0d31e4fbe18fb3364995be8c73426b83
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220757"
---
# <a name="no_dual_interfaces-import-attribute"></a>no_dual_interfaces 匯入屬性

**C++特殊**

變更編譯器產生雙重介面方法之包裝函式的方式。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***no_dual_interfaces**

## <a name="remarks"></a>備註

一般來說, 包裝函式會透過介面的虛擬函式資料表呼叫方法。 使用**no_dual_interfaces**時, 包裝函式`IDispatch::Invoke`會改為呼叫以叫用方法。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
