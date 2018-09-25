---
title: ATL 程式或控制項原始程式檔和標頭檔 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95fa6fa506e4f471b90d39659b0908e2755b72b0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398699"
---
# <a name="atl-program-or-control-source-and-header-files"></a>ATL 程式或控制項原始程式檔和標頭檔

當您在 Visual Studio 中建立 ATL 專案時，會根據您為所建立專案選取的選項而建立下列檔案。

這些檔案全都位於 *Projname* 目錄下，以及 [方案總管] 的標頭檔 (.h 檔案) 資料夾或原始程式檔 (.cpp 檔) 資料夾中。

|檔案名稱|描述|
|---------------|-----------------|
|*Projname*.h|包含 ATLSample.idl 中定義項目之 C++ 介面定義和 GUID 宣告的主要 Include 檔案。 它是由 MIDL 在編譯期間重新產生。|
|*Projname*.cpp|主要原始程式檔。 它包含您 DLL 匯出之同處理序伺服器的實作，以及本機伺服器的 `WinMain` 實作。 針對服務，這會另外實作所有服務管理功能。|
|偵錯工具|資源檔的標頭檔。|
|StdAfx.cpp|包含 StdAfx.h 和 Atlimpl.cpp 檔案。|
|StdAfx.h|包含 ATL 標頭檔。|

## <a name="see-also"></a>請參閱

[為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[MFC 程式或控制項原始程式檔和標頭檔](../ide/mfc-program-or-control-source-and-header-files.md)<br>
[CLR 專案](../ide/files-created-for-clr-projects.md)