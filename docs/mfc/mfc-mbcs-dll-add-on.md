---
title: MFC MBCS DLL 附加元件
ms.date: 12/02/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 522bd5cf573aa3a0b24f14bc50f23b0d0e300d2e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625355"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL 附加元件

在 Visual Studio 2013 和更新版本中 Visual Studio 安裝期間，支援 MFC 和其多位元組字元集（MBCS）程式庫需要額外的步驟。

**Visual Studio 2013**：根據預設，安裝在 Visual Studio 2013 中的 MFC 程式庫僅支援 Unicode 開發。 您需要 MBCS Dll，才能在將 [**字元集**] 屬性設定為 [**使用多位元組字元集**] 或 [**未設定**] 的 Visual Studio 2013 中，建立 MFC 專案。 下載[適用于 Visual Studio 2013 之多位元組 MFC 程式庫](https://www.microsoft.com/download/details.aspx?id=40770)的 DLL。

**Visual Studio 2015**： UNICODE 和 MBCS MFC dll 都包含在 Visual C++ 安裝程式元件中，但預設不會安裝 MFC 的支援。 Visual C++ 和 MFC 在 Visual Studio 安裝程式中是選擇性的安裝組態。 若要確定已安裝 MFC，請選擇安裝程式的 [自訂] **** ，然後在 [程式設計語言] **** 下，確定選取 [Visual C++] **** 和 [Microsoft Foundation Classes for C++] **** 。 如已安裝 Visual Studio，當您嘗試建立 MFC 專案時，系統會提示您安裝 Visual C++ 和/或 MFC。

**Visual Studio 2017 和更新版本**：當您從 Visual Studio 安裝程式程式的 [**選用元件**] 窗格中選取**MFC 和 ATL 支援**時，Unicode 和 MBCS MFC Dll 會與**使用 c + + 的桌面開發**工作負載一起安裝。 如果您的安裝不包含這些元件，請流覽至檔案 **|[新增專案**] 對話方塊，然後按一下 [**開啟 Visual Studio 安裝程式**] 連結。 如需詳細資訊，請參閱[Install Visual Studio](/visualstudio/install/install-visual-studio)。

## <a name="see-also"></a>另請參閱

[MFC 程式庫版本](mfc-library-versions.md)
