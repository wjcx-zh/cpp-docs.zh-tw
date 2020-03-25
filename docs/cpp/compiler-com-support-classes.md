---
title: 編譯器 COM 支援類別
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: a8b0845fdfa96c1cb4b8b67e9d39169d9f4d3737
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189698"
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
