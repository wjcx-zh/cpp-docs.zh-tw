---
title: "新的專案，從現有程式碼的原始程式檔 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.importwiz.location
dev_langs: C++
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 04f73f89745f797658029eac2331d1764af4c065
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>從現有的程式碼檔建立新專案精靈、指定專案位置和原始程式檔
您可以使用 [從現有的程式碼檔建立新專案精靈] 的此頁面來指定：  
  
-   新的專案的目錄路徑  
  
-   要搜尋現有的原始程式檔的目錄  
  
-   精靈將匯入到新的專案的檔案類型  
  
## <a name="task-list"></a>工作清單  
 [如何：從現有程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 清單  
 **專案檔位置**  
 指定新專案的目錄路徑。 這個位置是所有檔案和子目錄的新專案精靈將存放的位置。  
  
 **瀏覽**  
 顯示**專案檔位置**對話方塊，可協助您指定的目錄將包含新的專案。 這個控制項可讓您瀏覽至所要的資料夾。  
  
 **專案名稱**  
 指定新專案的名稱。 專案檔案，會使用例如.vcxproj 檔案延伸模組會採用此名稱。 現有的程式碼檔案會保留其原始名稱。  
  
 **從這些資料夾將檔案加入專案**  
 有選取時，設定精靈將從原始的目錄 （此控制項下方的清單方塊中指定） 的複製現有的程式碼檔案到新的專案。  
  
 **新增子資料夾**  
 指定要複製的程式碼檔案的目錄中所有子目錄列出**資料夾**到新的專案的資料行。  
  
 **資料夾**  
 表示包含現有的程式碼檔案複製到新的專案目錄的路徑。 此欄會列出所有精靈將會搜尋現有的程式碼檔案的目錄。  
  
 **[新增]**  
 顯示**從這個資料夾將檔案加入專案**對話方塊中，可幫助您精靈將會搜尋現有的程式碼檔案的指定目錄。  
  
 **移除**  
 刪除已在清單方塊的左邊此控制項中選取的目錄路徑。  
  
 **要加入至專案的檔案類型**  
 指定精靈會加入到新的專案，根據指定的副檔名的檔案的類型。 副檔名加上星號萬用字元，並以分號分隔的副檔名清單中。  
  
 **在 [方案總管] 中顯示所有檔案**  
 指定新的專案，才能看見並顯示在 [方案總管] 視窗中的所有檔案。 這個選項預設為啟用。