---
title: MFC MBCS DLL 附加元件 |Microsoft Docs
ms.custom: ''
ms.date: 1/04/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS
- MFC
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa6840fe54478b88e201dd09950917b95c7a1cc4
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2018
ms.locfileid: "39025730"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL 附加元件

MFC 的支援，以及其多位元組字元集 (mbcs) 程式庫請在 Visual Studio 2013、 2015年和 2017年的 Visual Studio 安裝期間需要額外的步驟。

**Visual Studio 2013**： 根據預設，安裝 Visual Studio 2013 中的 MFC 程式庫僅支援 Unicode 開發。 您需要 MBCS Dll，才能建置 MFC 專案中擁有的 Visual Studio 2013**字元集**屬性設定為**使用多位元組字元集**或是**未設定**。 下載在 DLL [Multibyte MFC Library for Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770)。

**Visual Studio 2015**： 兩者的 Unicode 和 MBCS MFC Dll 會隨附於 Visual c + + 安裝程式元件，但預設並未安裝 MFC 的支援。 Visual C++ 和 MFC 在 Visual Studio 安裝程式中是選擇性的安裝組態。 若要確定已安裝 MFC，請選擇安裝程式的 [自訂]  ，然後在 [程式設計語言] 下，確定選取 [Visual C++]  和 [Microsoft Foundation Classes for C++]  。 如已安裝 Visual Studio，當您嘗試建立 MFC 專案時，系統會提示您安裝 Visual C++ 和/或 MFC。

**Visual Studio 2017**: Unicode 和 MBCS MFC Dll 會隨**使用 c + + 的桌面開發**當您選取的工作負載**MFC 和 ATL 支援**從**選擇性元件**窗格。 如果您的安裝不包含這些元件，瀏覽至**檔案 |新的專案**對話方塊，再按一下**開啟 Visual Studio 安裝程式**連結。

## <a name="see-also"></a>另請參閱

[MFC 程式庫版本](../mfc/mfc-library-versions.md)

