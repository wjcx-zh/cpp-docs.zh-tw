---
title: 相容性
description: 說明 Microsoft 通用 C 執行時間程式庫（UCRT）與標準 C 程式庫（POSIX、Safe CRT 和 Store 應用程式）的相容性。
ms.date: 12/06/2019
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
ms.openlocfilehash: fba85462218d0cc2ba1d52caa4e59b2cfb9f4fd6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443493"
---
# <a name="compatibility"></a>相容性

通用 C 執行階段程式庫 (UCRT) 支援與 C++ 相容所需的大部分 C 標準程式庫。 它會執行 C99 （ISO/IEC 9899:1999）程式庫，但有一些例外狀況：定義于 \<tgmath.h> 中的類型一般宏 >，以及 \<complex > 中的嚴格類型相容性。 UCRT 也會執行 POSIX 的大型子集（ISO/IEC 9945-1:1996，POSIX 系統應用程式介面） C 程式庫。 不過，它並不完全符合任何特定的 POSIX 標準。 UCRT 也會執行數個不屬於標準的 Microsoft 特定函式和宏。

Microsoft Visual C++ 實作特有的函式可在 vcruntime 程式庫中找到。  這些函式中的許多都是供內部使用，而且不能由使用者程式碼呼叫。 有一部分會記載在說明中，供偵錯及實作相容性之用。

C++ 標準在全域命名空間中，會保留以底線開頭的名稱供實作之用。 POSIX 函式和 Microsoft 特定執行時間程式庫函式都在全域命名空間中，但不是標準 C 執行時間程式庫的一部分。 這就是為什麼這些函式的慣用 Microsoft 實作為開頭底線的原因。 為了確保可攜性，UCRT 也能支援預設名稱，但當使用這些名稱的程式碼遭到編譯時，Microsoft C++ 編譯器仍會發出已淘汱的警告。 只有預設名稱會被取代，而不是函式本身。 若要停止顯示警告，請先定義 `_CRT_NONSTDC_NO_WARNINGS` ，然後再將標頭加入使用原始 POSIX 名稱的程式碼中。

標準 C 程式庫中有某些函式曾因為誤用參數及未檢查緩衝區而有使用方式不安全的記錄。 這些函式通常是程式碼中安全性問題的來源。 Microsoft 建立了這些函式的一組安全版本，這些功能會驗證參數的使用方式。 當執行時間偵測到問題時，它們會叫用不正確參數處理常式。  根據預設，當現行函式有更安全的變體可供使用時，Microsoft C++ 編譯器便會發出已淘汱的警告。 當您將程式碼編譯C++為時，您可以將 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定義為1，以排除大部分的警告。 此宏可讓樣板多載呼叫更安全的變體，同時維持可移植的原始程式碼。 若要停止顯示警告，請先定義 `_CRT_SECURE_NO_WARNINGS` ，然後再將標頭加入使用這些函式的程式碼中。 如需詳細資訊，請參閱 [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md)。

除了文件中所述有關這些特殊函式的相關資訊之外，UCRT 也相容於 Windows API。  Windows Store 或通用 Windows 平臺（[UWP](/uwp)）應用程式中不支援某些功能。 這些函式會列在[通用 Windows 平臺應用程式中不支援的 CRT](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)函式中。

## <a name="related-articles"></a>相關文章

|Title|描述|
|-----------|-----------------|
|[UWP 應用程式、Windows 執行階段及 C 執行階段](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|描述 UCRT 常式與通用 Windows 應用程式或 Microsoft Store 應用程式不相容的時機。|
|[ANSI C 合規性](../c-runtime-library/ansi-c-compliance.md)|說明 UCRT 中符合標準的命名。|
|[UNIX](../c-runtime-library/unix.md)|提供移植程式至 UNIX 的指導方針。|
|[Windows 平台 (CRT)](../c-runtime-library/windows-platforms-crt.md)|列出此 CRT 支援的作業系統。|
|[回溯相容性](../c-runtime-library/backward-compatibility.md)|描述如何將舊的 CRT 名稱對應到新的 CRT 名稱。|
|[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)|提供 CRT 程式庫 (.lib) 檔案和相關聯之編譯器選項的概觀。|