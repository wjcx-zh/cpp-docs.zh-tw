---
title: 編譯器 COM 支援類別
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 1a9ff7c57965c9ba00881d5fe48501a6138b31d1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444429"
---
# <a name="compiler-com-support-classes"></a>編譯器 COM 支援類別

**Microsoft 專屬**

標準類別用來支援某些 COM 類型。 類別定義于 \<comdef.h 中，> 和從類型程式庫產生的標頭檔。

|類別|目的|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|包裝 `BSTR` 類型可提供有用的運算子和方法。|
|[_com_error](../cpp/com-error-class.md)|定義在大多數失敗中[_com_raise_error](../cpp/com-raise-error.md)擲回的錯誤物件。|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|封裝 COM 介面指標，並將 `AddRef`、`Release`和 `QueryInterface`所需的呼叫自動化。|
|[_variant_t](../cpp/variant-t-class.md)|包裝 `VARIANT` 類型可提供有用的運算子和方法。|

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援](../cpp/compiler-com-support.md)<br/>
[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)