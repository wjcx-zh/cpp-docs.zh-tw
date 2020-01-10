---
title: raw_dispinterfaces 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 73c58b72b27de8dcf96e8ab9464d0fb6bce12b66
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216220"
---
# <a name="raw_dispinterfaces-import-attribute"></a>raw_dispinterfaces 匯入屬性

**C++特殊**

告訴編譯器針對分配介面方法, 以及呼叫`IDispatch::Invoke`和傳回 HRESULT 錯誤碼的屬性, 產生低層級的包裝函式。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***raw_dispinterfaces**

## <a name="remarks"></a>備註

如果未指定此屬性, 則只會產生高階包裝函式, 這C++會在失敗時擲回例外狀況。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
