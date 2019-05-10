---
title: MFC MBCS DLL 附加元件
ms.date: 05/08/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 20145b200a0f8bac8ccb461331d4d233a3b0251e
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524823"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL 附加元件

MFC 的支援，以及其多位元組字元集 (mbcs) 程式庫請在 Visual Studio 2013 和更新版本的 Visual Studio 安裝期間需要額外的步驟。

**Visual Studio 2013**:根據預設，安裝 Visual Studio 2013 中的 MFC 程式庫僅支援 Unicode 開發。 您需要 MBCS Dll，才能建置 MFC 專案中擁有的 Visual Studio 2013**字元集**屬性設定為**使用多位元組字元集**或是**未設定**。 下載在 DLL [Multibyte MFC Library for Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770)。

**Visual Studio 2015**：Unicode 和 MBCS MFC Dll 包含在視覺效果C++安裝程式元件，但預設並未安裝 MFC 的支援。 Visual C++ 和 MFC 在 Visual Studio 安裝程式中是選擇性的安裝組態。 若要確定已安裝 MFC，請選擇安裝程式的 [自訂]  ，然後在 [程式設計語言] 下，確定選取 [Visual C++]  和 [Microsoft Foundation Classes for C++]  。 如已安裝 Visual Studio，當您嘗試建立 MFC 專案時，系統會提示您安裝 Visual C++ 和/或 MFC。

**Visual Studio 2017 及更新版本**：Unicode 和 MBCS MFC Dll 會隨**使用的桌面開發C++** 當您選取的工作負載**MFC 和 ATL 支援**從**選用元件**窗格。 如果您的安裝不包含這些元件，瀏覽至**檔案 |新的專案**對話方塊，再按一下**開啟 Visual Studio 安裝程式**連結。

## <a name="see-also"></a>另請參閱

[MFC 程式庫版本](../mfc/mfc-library-versions.md)
