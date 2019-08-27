---
title: 嚴重錯誤 C1510
ms.date: 04/11/2017
f1_keywords:
- C1510
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
ms.openlocfilehash: 33c17a3099f4aed99cc26579d0e65c4a350b4268
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501085"
---
# <a name="fatal-error-c1510"></a>嚴重錯誤 C1510

無法開啟語言資源 clui.dll

編譯器無法載入語言資源 DLL。

此問題有兩個常見的原因。 使用32位編譯器和工具時, 您可能會在連結期間使用超過 2 GB 記憶體的大型專案看到此錯誤。 64位 Windows 系統上的可能解決方案是使用64位原生或跨編譯器和工具來產生您的程式碼。 這會利用可供64位應用程式使用的較大記憶體空間。 如果您必須使用32位編譯器, 因為您是在32位系統上執行, 在某些情況下, 您可以將連結器可用的記憶體數量增加到3GB。 如需詳細資訊, [請參閱 4 gb 調整:Bcdedit 和 boot.ini](/windows/win32/memory/4-gigabyte-tuning)和[bcdedit/set increaseuserva](/windows-hardware/drivers/devtest/bcdedit--set)命令。

另一個常見的原因是 Visual Studio 安裝中斷或不完整。 在此情況下, 請再次執行安裝程式, 以修復或重新安裝 Visual Studio。
