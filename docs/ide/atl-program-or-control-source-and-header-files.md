---
title: ATL 程式或控制項原始檔和標頭檔 |Microsoft 文件
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
ms.openlocfilehash: 3e8e5065cebab002e9c48aef560eb9f2feab67e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="atl-program-or-control-source-and-header-files"></a>ATL 程式或控制項原始程式檔和標頭檔
當您建立的 ATL 專案在 Visual Studio 中，根據您選取您建立專案的選項時，會建立下列檔案。  
  
 所有這些檔案位於*Projname*目錄下，而標頭檔 （.h 檔案） 的資料夾或方案總管 中的原始程式檔 （.cpp 檔） 資料夾中。  
  
|檔案名稱|描述|  
|---------------|-----------------|  
|*Projname*.h|主要的 include 檔案包含的 c + + 介面定義和 GUID 宣告 ATLSample.idl 中定義的項目。 它是由 MIDL 重新產生在編譯期間。|  
|*Projname*.cpp|主要原始程式檔。 它包含您的 DLL 匯出的處理序伺服器的實作的`WinMain`本機伺服器。 服務中，這會另外實作所有服務管理功能。|  
|偵錯工具|資源檔標頭檔。|  
|StdAfx.cpp|包含 StdAfx.h 和 Atlimpl.cpp 檔案。|  
|StdAfx.h|包含 ATL 標頭檔。|  
  
## <a name="see-also"></a>另請參閱  
 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [MFC 程式或控制項原始檔和標頭檔](../ide/mfc-program-or-control-source-and-header-files.md)   
 [CLR 專案](../ide/files-created-for-clr-projects.md)