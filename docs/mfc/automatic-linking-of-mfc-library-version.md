---
title: "MFC 程式庫版本的自動連結 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: defaultlib
dev_langs: C++
helpviewer_keywords:
- defaultlib in MFC
- automatic links [MFC]
- MFC libraries, linking to
- linking [MFC], automatic of MFC library version
- linking [MFC]
- linking [MFC], of MFC
- MFC libraries, versions
ms.assetid: 02af4a20-2034-4fce-b200-c2202c3c8311
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ddc156d8518318a686796a25e89ee84a9a67ee59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="automatic-linking-of-mfc-library-version"></a>MFC 程式庫版本的自動連結
在 3.0 版之前 (Visual C++ 2.0 版之前) 的各個 MFC 版本中，您必須為連結器在程式庫的輸入清單中手動指定正確版本的 MFC 程式庫。 MFC 3.0 版和更新版本中，不再需要手動指定 MFC 程式庫版本。 相反地，MFC 標頭檔會自動判斷正確版本的 MFC 程式庫中，根據值以定義`#define`，例如**_DEBUG**或**_UNICODE**。 MFC 標頭檔新增**/defaultlib**指示詞，指示連結器連結特定版本的 MFC 程式庫。  
  
 例如，AFX.H 標頭檔的下列程式碼片段會根據您是否使用 MFC 偵錯版本，指示連結器連結 MFC NAFXCWD.LIB 或 NAFXCW.LIB 版本的 MFC：  
  
```c++
#ifndef _UNICODE 
#ifdef _DEBUG
#pragma comment(lib, "nafxcwd.lib")
#else
#pragma comment(lib, "nafxcw.lib")
#endif
#else
#ifdef _DEBUG
#pragma comment(lib, "uafxcwd.lib")
#else
#pragma comment(lib, "uafxcw.lib")
#endif
#endif
```  
  
 MFC 標頭檔也會連結所有必要的程式庫，包括 MFC 程式庫、Win32 程式庫、OLE 程式庫、從範例建置的 OLE 程式庫、ODBC 程式庫等。 Win32 程式庫包含 Kernel32.Lib、User32.Lib 和 GDI32.Lib。  
  
## <a name="see-also"></a>請參閱  
 [MFC 程式庫版本](../mfc/mfc-library-versions.md)

