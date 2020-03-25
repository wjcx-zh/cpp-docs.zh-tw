---
title: 專案建置錯誤 PRJ0003
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: 59028c6d886630ef7db115a2ea93327669b2fcfd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192922"
---
# <a name="project-build-error-prj0003"></a>專案建置錯誤 PRJ0003

> 產生「*命令列*」時發生錯誤。

從 [**屬性頁**] 對話方塊中的輸入所形成的*命令列*命令會傳回錯誤碼，但**輸出**視窗中不會出現任何資訊。

此錯誤的可能原因包括：

- 您的專案相依于 ATL Server。 從 Visual Studio 2008 開始，已不再包含 ATL Server 做為 Visual Studio 的一部分，但已發行為 CodePlex 的共用來源專案。 若要下載 ATL Server 原始程式碼和工具，請移至[Atl 伺服器程式庫和工具](https://go.microsoft.com/fwlink/p/?linkid=81979)。

- 系統資源不足。 關閉一些應用程式以解決此問題。

- 安全性許可權不足。 請確認您有足夠的安全性許可權。

- **VC + + 目錄**中指定的可執行檔路徑不包含您嘗試執行之工具的路徑。 如需相關資訊，請參閱[設定編譯器和組建屬性](../../build/working-with-project-properties.md)

- 對於 makefile 專案，您缺少在任一**組建命令列**或**重建命令列**上執行的命令。

## <a name="see-also"></a>另請參閱

[專案建置錯誤和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
