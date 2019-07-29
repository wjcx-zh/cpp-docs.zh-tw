---
title: 編譯器 COM 支援
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 421930088dcbf9762d50b5af37d994b9008890eb
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606372"
---
# <a name="compiler-com-support"></a>編譯器 COM 支援

## <a name="microsoft-specific"></a>Microsoft 特定的

Microsoft C++編譯器可以直接讀取元件物件模型 (COM) 類型程式庫, 並將內容轉譯C++成可包含在編譯中的原始程式碼。 語言延伸模組可用來加速桌面應用程式用戶端上的 COM 程式設計。

藉由使用[#import 預處理器](../preprocessor/hash-import-directive-cpp.md)指示詞, 編譯器可以讀取類型程式庫, 並將它C++轉換成標頭檔, 將 COM 介面描述為類別。 一組 `#import` 屬性可供使用者控制產生類別程式庫標頭檔的內容。

您可以使用[__declspec](../cpp/declspec.md)擴充屬性[UUID](../cpp/uuid-cpp.md)來指派 COM 物件的全域唯一識別碼 (GUID)。 關鍵字[__uuidof](../cpp/uuidof-operator.md)可以用來解壓縮與 COM 物件相關聯的 GUID。 另一個 **__declspec**屬性 ( [property](../cpp/property-cpp.md)) 可以用來指定 COM `get`物件`set`之資料成員的和方法。

提供一組 COM 支援全域函式和類別, 以支援`VARIANT`和`BSTR`類型、執行智慧型指標, 以及封裝`_com_raise_error`所擲回的錯誤物件:

- [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)<br/>
[編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)
