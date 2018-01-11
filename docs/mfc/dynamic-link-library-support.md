---
title: "動態連結程式庫支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- regular MFC DLLs [MFC], project targets as DLLs
- DLLs [MFC], MFC
- NAFXDW.LIB
- MFC DLLs [MFC], regular MFC DLLs
- USRDLLs, DLL support
- NAFXDWD.LIB
ms.assetid: cc31c69f-3c78-4db1-9ecd-0fd8dc3217e3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 394c48644c3b5cdc2514fefef2f4451e4098856f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dynamic-link-library-support"></a>動態連結程式庫支援
NAFXCW.lib 和 NAFXCWD.lib 文件庫 (靜態連結程式庫命名慣例表中所列[程式庫命名慣例](../mfc/library-naming-conventions.md)) 建立您的專案為動態連結程式庫，稱為 「 標準 MFC DLL 」 (先前稱為 「 USRDLL")可以搭配不會建置類別庫的應用程式。 這個 DLL 不支援相同 MFCx0.DLL 和 MFCx0D.DLL （又稱為 AFXDLL），其中包含整個類別庫 DLL 中。 如需詳細資訊，請參閱[Dll](../build/dlls-in-visual-cpp.md)。 DLL 名稱的資料表，請參閱[MFC Dll 命名慣例](../build/naming-conventions-for-mfc-dlls.md)。  
  
## <a name="see-also"></a>請參閱  
 [MFC 程式庫版本](../mfc/mfc-library-versions.md)

