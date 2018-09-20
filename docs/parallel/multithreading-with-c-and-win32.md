---
title: 使用 C 和 Win32 進行多執行緒處理 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09397b5a60dcc2cbe2b3e6265f6080f3c5c1e212
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428092"
---
# <a name="multithreading-with-c-and-win32"></a>使用 C 和 Win32 進行多執行緒處理

Microsoft Visual c + + 來建立多執行緒應用程式提供支援。 您應該考慮使用多個執行緒，如果您的應用程式需要執行耗費資源的作業，會導致使用者介面變得沒有回應。

Visual c + + 中，有多個執行緒在程式的兩種方式： 使用 Microsoft Foundation Class (MFC) 程式庫或 C 執行階段程式庫和 Win32 API。 使用 MFC 建立多執行緒應用程式的詳細資訊，請參閱[c + + 和 MFC 的多執行緒](multithreading-with-cpp-and-mfc.md)閱讀下列有關在 c 中的多執行緒主題之後

這些主題會說明 Visual c + + 中支援多執行緒程式建立的功能。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [項目多執行緒即將](multithread-programs.md)

- [程式庫支援來進行多執行緒處理](library-support-for-multithreading.md)

- [包含的檔案進行多執行緒處理](include-files-for-multithreading.md)

- [執行緒控制的 C 執行階段程式庫函式](c-run-time-library-functions-for-thread-control.md)

- [在 C 中的多執行緒程式範例](sample-multithread-c-program.md)

- [撰寫多執行緒 Win32 程式](writing-a-multithreaded-win32-program.md)

- [編譯和連結多執行緒程式](compiling-and-linking-multithread-programs.md)

- [避免具有多執行緒程式的問題區域](avoiding-problem-areas-with-multithread-programs.md)

- [執行緒區域儲存區 (TLS)](thread-local-storage-tls.md)

## <a name="see-also"></a>另請參閱

[舊版程式碼的多執行緒支援 (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)