---
title: 編譯器 COM 支援
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: f0b1d6280dc27641287de8fe539cd3a148048245
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646039"
---
# <a name="compiler-com-support"></a>編譯器 COM 支援

## <a name="microsoft-specific"></a>Microsoft 特定的

Visual C++ 編譯器可直接讀取元件物件模型 (COM) 類型程式庫，以及內容轉譯成可在編譯時包含的 C++ 原始程式碼。 語言擴充功能可協助您進行用戶端的 COM 程式設計。

藉由使用[#import 前置處理器指示詞](../preprocessor/hash-import-directive-cpp.md)，編譯器可以讀取類型程式庫，並轉換到 c + + 標頭檔，描述 COM 介面必須標記為類別。 一組 `#import` 屬性可供使用者控制產生類別程式庫標頭檔的內容。

您可以使用[__declspec](../cpp/declspec.md)擴充的屬性[uuid](../cpp/uuid-cpp.md)指派全域唯一識別碼 (GUID) 至 COM 物件。 關鍵字[__uuidof](../cpp/uuidof-operator.md)可以用來擷取與 COM 物件相關聯的 GUID。 另一個 **__declspec**屬性，[屬性](../cpp/property-cpp.md)，可以用來指定`get`和`set`COM 物件的資料成員的方法。

一組 COM 支援全域函式和類別提供來支援`VARIANT`並`BSTR`型別實作智慧型指標，以及封裝所擲回的錯誤物件`_com_raise_error`:

- [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)<br/>
[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)