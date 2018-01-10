---
title: "MFC 中的 Unicode |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- wide characters, Unicode
- Unicode [MFC], MFC
- wide characters, encoding
- strings [MFC], Unicode
- Unicode [MFC], enabling
ms.assetid: 1002004b-4113-4380-bf63-e1570934b793
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c1a104ffc30a7463d640f63d26f7a80faad333b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-in-mfc"></a>MFC 中的 Unicode
MFC 支援 Windows NT、Windows 2000 和 Windows XP 平台上編碼寬字元的 Unicode 標準。 Unicode 應用程式無法在 Windows 98 平台上執行。  
  
 MFC 程式庫的 Unicode 版本如下所示：  
  
### <a name="static-link-libraries"></a>靜態連結程式庫  
  
|發行|偵錯|描述|  
|-------------|-----------|-----------------|  
|UAFXCW.lib、.pdb|UAFXCWD.lib、.pdb|Unicode MFC 靜態連結程式庫|  
  
### <a name="dynamic-link-libraries"></a>動態連結程式庫  
  
|發行|偵錯|描述|  
|-------------|-----------|-----------------|  
|MFC100U.lib、.dbg、def、.dll、.map、.pdb、.prf|MFC100UD.lib、.def、.dll、.map、.pdb|Unicode MFC 匯入程式庫 (副檔名的說明請參閱下方的備註)|  
|MFCS100U.lib、.pdb|MFCS100UD.lib、.pdb|Unicode MFC 匯入程式庫包含必須在應用程式或 DLL 中以靜態方式連結的程式碼。|  
  
 **檔案類型**  
  
-   匯入程式庫檔案的副檔名為 (.lib)。  
  
-   動態連結程式庫檔案的副檔名為 (.dll)。  
  
-   模組定義 (.def) 檔案是一些包含定義 .exe 或 .dll 陳述式的文字檔。  
  
-   對應 (.map) 檔案是一些包含在連結程式時使用之連結器資訊的文字檔。  
  
-   程式庫 (.lib) 檔案會與 MFC 的 DLL 版本搭配使用。 這些檔案包含在應用程式或 DLL 中必須以靜態方式連結的程式碼。  
  
-   程式資料庫 (.pdb) 檔案包含偵錯和專案狀態資訊。  
  
-   偵錯 (.dbg) 檔案包含 Visual C++ 偵錯工具使用的相關資訊 (COFF FPO 和 CodeView)。  
  
 如需命名慣例的詳細資訊，請參閱[程式庫命名慣例](../mfc/library-naming-conventions.md)。  
  
 如需使用 Unicode 和 MFC 資訊，請參閱[字串： Unicode 和多位元組字元集 (MBCS) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
## <a name="see-also"></a>請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)

