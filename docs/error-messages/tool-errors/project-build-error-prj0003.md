---
title: 專案建置錯誤 PRJ0003
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: a6530045870573921cf626ceeec4c1dca10cdbfb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816174"
---
# <a name="project-build-error-prj0003"></a>專案建置錯誤 PRJ0003

> 錯誤繁衍 '*命令列*'。

*命令列*格式，從輸入中的命令**屬性頁** 對話方塊中傳回的錯誤碼，但會顯示任何資訊**輸出**視窗。

此錯誤的可能原因包括：

- 您的專案相依於 ATL Server。 從 Visual Studio 2008 中，ATL Server 已不再屬於 Visual Studio 中，但已發行為 CodePlex 的共用原始碼專案。 若要下載 ATL Server 原始程式碼和工具，請前往[ATL 伺服器程式庫和工具](http://go.microsoft.com/fwlink/p/?linkid=81979)。

- 系統資源不足。 關閉一些應用程式，以解決此問題。

- 安全性權限不足。 請確認您有足夠的安全性權限。

- 可執行檔中指定的路徑**VC + + 目錄**不包含您嘗試執行此工具的路徑。 如需資訊，請參閱[設定編譯器和組建屬性](../../build/working-with-project-properties.md)

- Makefile 專案中，您沒有要在其中執行的命令**建置命令列**或是**重建命令列**。

## <a name="see-also"></a>另請參閱

[專案建置錯誤和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)