---
title: MFC MBCS DLL 附加元件
ms.date: 12/02/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: fe74e0639664b6a6a86a4c3269f174de441002f4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810365"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL 附加元件

在 Visual Studio 2013 和更新版本中 Visual Studio 安裝期間，支援 MFC 和其多位元組字元集（MBCS）程式庫需要額外的步驟。

**Visual Studio 2013**：根據預設，安裝在 Visual Studio 2013 中的 MFC 程式庫僅支援 Unicode 開發。 您需要 MBCS Dll，才能在將 [**字元集**] 屬性設定為 [**使用多位元組字元集**] 或 [**未設定**] 的 Visual Studio 2013 中，建立 MFC 專案。 下載[適用于 Visual Studio 2013 之多位元組 MFC 程式庫](https://www.microsoft.com/download/details.aspx?id=40770)的 DLL。

**Visual Studio 2015**： Visual C++ Setup 元件中包含 Unicode 和 MBCS MFC dll，但預設不會安裝 MFC 的支援。 Visual C++ 和 MFC 在 Visual Studio 安裝程式中是選擇性的安裝組態。 若要確定已安裝 MFC，請選擇安裝程式的 [自訂] ，然後在 [程式設計語言]下，確定選取 [Visual C++] 和 [Microsoft Foundation Classes for C++] 。 如已安裝 Visual Studio，當您嘗試建立 MFC 專案時，系統會提示您安裝 Visual C++ 和/或 MFC。

**Visual Studio 2017 和更新版本**：當您從 Visual Studio 安裝程式程式的 [**選用元件**] 窗格中選取**MFC 和 ATL 支援**時，Unicode 和 MBCS MFC dll 會與使用**C++** 工作負載的桌面開發一併安裝。 如果您的安裝不包含這些元件，請流覽至檔案 **|[新增專案**] 對話方塊，然後按一下 [**開啟 Visual Studio 安裝程式**] 連結。 如需詳細資訊，請參閱[Install Visual Studio](/visualstudio/install/install-visual-studio)。

## <a name="see-also"></a>請參閱

[MFC 程式庫版本](../mfc/mfc-library-versions.md)
