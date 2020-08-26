---
title: 在 Windows 上執行 Linux 程式
ms.date: 07/31/2019
helpviewer_keywords:
- Linux [C++], porting to Win32
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: f13777c1c366d2f6b9497296f8819454dda7647e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837043"
---
# <a name="running-linux-programs-on-windows"></a>在 Windows 上執行 Linux 程式

若要在 Windows 上執行 Linux 程式，有下列方式供您選擇：

- 在適用於 Linux 的 Windows 子系統 (WSL) 上以原樣執行程式。 在 WSL 中，您的程式會直接在電腦硬體上執行，而不是在虛擬機器中執行。 WSL 也可讓您在 Windows 與 Linux 系統之間直接進行 filesystem 呼叫，而不需要 SSL 傳輸。 WSL 設計成命令列環境，不建議用於處理大量圖形的應用程式。 如需詳細資訊，請參閱[適用於 Linux 的 Windows 子系統文件](/windows/wsl/about)。
- 在您的本機電腦或 Azure 上，於 Linux 虛擬機器或 Docker 容器中以原樣執行程式。 如需詳細資訊，請參閱[虛擬機器](https://azure.microsoft.com/services/virtual-machines/)和 [Azure 上的 Docker](/azure/docker/)。
- 在 [MinGW](http://MinGW.org/) 或 [MinGW-w64](https://sourceforge.net/p/mingw-w64/wiki2/Home/) 環境中使用 gcc 或 clang 編譯程式，這些環境提供從 Linux 到 Windows 系統呼叫的轉譯層。
- 在 [Cygwin](https://www.cygwin.com/) 環境中使用 gcc 或 clang 編譯並執行程式，這個環境相較於 MinGW 或 MinGW-w64，在 Windows 上提供更完整的 Linux 環境。
- 從 Linux 手動移植程式碼，然後使用 Microsoft C++ (MSVC) 為 Windows 進行編譯。 這牽涉到把不受平台影響的程式碼重構成不同的程式庫，然後重新撰寫 Linux 專用程式碼，以使用 Windows 專用程式碼 (例如 Win32 或 DirectX API)。 對於需要高效能圖形的應用程式而言，這可能是最佳選項。
