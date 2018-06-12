---
title: 從現有程式碼新增專案 - 原始程式檔 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.location
dev_langs:
- C++
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d85a7b85996ed307596865a31d55cf4b119e5bd5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338691"
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>從現有的程式碼檔建立新專案精靈、指定專案位置和原始程式檔
使用 [從現有的程式碼檔建立新專案精靈] 的這個頁面來指定：  
  
-   新專案的目錄路徑  
  
-   用來搜尋現有原始程式檔的目錄  
  
-   精靈將匯入到新專案的檔案類型  
  
## <a name="task-list"></a>工作清單  
 [如何：從現有程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 清單  
 [專案檔位置]  
 指定新專案的目錄路徑。 這個位置是精靈存放新專案之所有檔案 (和子目錄) 的位置。  
  
 **瀏覽**  
 顯示 [專案檔位置] 對話方塊，其可協助您指定將包含新專案的目錄。 這個控制項可讓您巡覽至所需的資料夾。  
  
 **專案名稱**  
 指定新專案的名稱。 具有如 .vcxproj 等副檔名的專案檔會採用此名稱。 現有的程式碼檔案會保留其原始名稱。  
  
 [從這些資料夾將檔案新增至專案]  
 核取時，會設定精靈以將現有的程式碼檔案從其原始目錄 (在此控制項下方的清單方塊中指定) 複製到新專案。  
  
 [新增子資料夾]  
 指定要將程式碼檔案從 [資料夾] 資料行所列出之目錄的所有子目錄中複製到新專案。  
  
 [資料夾]  
 表示包含要複製到新專案之現有程式碼檔案的目錄路徑。 此資料行會列出精靈將搜尋現有程式碼檔案的所有目錄。  
  
 **[新增]**  
 顯示 [從這個資料夾將檔案新增至專案中] 對話方塊，其可協助您指定精靈將搜尋現有程式碼檔案的目錄。  
  
 **移除**  
 刪除已在此控制項左邊的清單方塊中選取的目錄路徑。  
  
 **要新增至專案的檔案類型**  
 指定精靈將根據指定的副檔名新增至新專案的檔案類型。 副檔名前面會加上星號萬用字元，並在副檔名清單中以分號分隔。  
  
 **在方案總管中顯示所有檔案**  
 指定要在 [方案總管] 視窗中看見並顯示新專案中的所有檔案。 這個選項預設為啟用。