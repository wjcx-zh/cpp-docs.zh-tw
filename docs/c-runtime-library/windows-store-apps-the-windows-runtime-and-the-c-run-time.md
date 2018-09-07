---
title: UWP 應用程式、Windows 執行階段和 C 執行階段 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78f76b6f61eb5d8e7370e61e9cc1f466bdfb4c43
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592715"
---
# <a name="uwp-apps-the-windows-runtime-and-the-c-run-time"></a>UWP 應用程式、Windows 執行階段和 C 執行階段

通用 Windows 平台 (UWP) 應用程式是在 Windows 執行階段 (執行於 Windows 8) 中執行的程式。 Windows 執行階段是可信賴的環境，控制可供 UWP 應用程式使用的函式、變數及資源。 不過，根據設計，Windows 執行階段限制會讓大多數的 C 執行階段程式庫 (CRT) 功能無法在 UWP 應用程式中使用。

「Windows 執行階段」不支援下列 CRT 功能：

- 與不支援的功能相關之大部分 CRT 函式。

   例如，UWP 應用程式無法使用 **exec** 和 **spawn** 系列常式來建立處理序。

   當 CRT 函式不受 UWP 應用程式支援時，該事實會記載在其參考文件中。

- 大部分的多位元組字元和字串的函式。

   不過，Unicode 和 ANSI 文字皆受到支援。

- 主控台應用程式和命令列引數。

   不過，傳統型應用程式仍然支援主控台和命令列引數。

- 環境變數。

- 目前工作目錄的概念。

- 與 CRT 靜態連結並使用 [/MT](../build/reference/md-mt-ld-use-run-time-library.md) 或 `/MTd` 編譯器選項建置的 UWP 應用程式和 DLL。

   也就是使用 CRT 的多執行緒、靜態版本的應用程式。

- 使用 [/MDd](../build/reference/md-mt-ld-use-run-time-library.md) 編譯器選項建置的應用程式。

   也就是說，CRT 的偵錯、多執行緒和特定 DLL 的版本。 Windows 執行階段不支援這類應用程式。

如需於 UWP 應用程式中無法使用的 CRT 函式完整清單與替代函式建議，請參閱 [CRT functions not supported in Universal Windows Platform apps](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="see-also"></a>請參閱

[相容性](../c-runtime-library/compatibility.md)<br/>
[Windows 執行階段不支援的 CRT 函式](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)<br/>
[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
