---
title: 編譯器 COM 支援類別
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: 066fe797bc500625e96e027777a70f278b88cddb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399196"
---
# <a name="compiler-com-support-classes"></a>編譯器 COM 支援類別

**Microsoft 專屬**

標準類別用來支援某些 COM 類型。 類別定義在\<comdef.h > 以及產生自類型程式庫標頭檔。

|類別|用途|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|包裝 `BSTR` 類型可提供有用的運算子和方法。|
|[_com_error](../cpp/com-error-class.md)|定義所擲回的錯誤物件[_com_raise_error](../cpp/com-raise-error.md)中最常見的失敗。|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|封裝 COM 介面指標，以及自動化所需的呼叫`AddRef`， `Release`，和`QueryInterface`。|
|[_variant_t](../cpp/variant-t-class.md)|包裝 `VARIANT` 類型可提供有用的運算子和方法。|

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援](../cpp/compiler-com-support.md)<br/>
[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)