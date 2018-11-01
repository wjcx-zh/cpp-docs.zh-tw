---
title: 嚴重錯誤 C1510
ms.date: 04/11/2017
f1_keywords:
- C1510
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
ms.openlocfilehash: f05f79ea78958a7d7a64f24bdce2d1151b93cdfb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596231"
---
# <a name="fatal-error-c1510"></a>嚴重錯誤 C1510

無法開啟語言資源 clui.dll

編譯器無法載入語言資源 DLL。

有兩個常見的原因，此問題。 使用 32 位元編譯器和工具時，您可能會看到此錯誤在連結期間使用超過 2 GB 的記憶體的大型專案。 在 64 位元 Windows 系統上可能的解決方案是使用 64 位元原生或跨編譯器和工具來產生您的程式碼。 這會利用 64 位元應用程式提供較大的記憶體空間。 如果因為您執行 32 位元系統上，您必須使用 32 位元編譯器，在某些情況下您可以提高連結器將 3 GB 的可用記憶體數量。 如需詳細資訊，請參閱 < [4 Gb 微調： BCDEdit 與 Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473)並[BCDEdit /set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx)命令。

其他常見的原因是損毀或不完整的 Visual Studio 安裝。 在此情況下，執行一次來修復或重新安裝 Visual Studio 安裝程式。
