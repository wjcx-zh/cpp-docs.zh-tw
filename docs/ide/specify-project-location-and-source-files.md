---
title: "從現有的程式碼檔建立新專案精靈、指定專案位置和原始程式檔 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.importwiz.location"
dev_langs: 
  - "C++"
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從現有的程式碼檔建立新專案精靈、指定專案位置和原始程式檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 \[從現有的程式碼檔建立新專案\] 精靈的這個頁面指定︰  
  
-   新專案的目錄路徑  
  
-   搜尋現有原始程式檔的目錄  
  
-   精靈將匯入新專案中的檔案類型  
  
## 工作清單  
 [如何：從現有程式碼建立 C\+\+ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## UIElement 清單  
 **專案檔位置**  
 指定新專案的目錄路徑。  這個位置是精靈將存放新專案的所有檔案 \(和子目錄\) 的位置。  
  
 **瀏覽**  
 顯示 \[**專案檔位置**\] 對話方塊，協助您指定將包含新專案的目錄。  這個控制項可讓您巡覽至所要的資料夾。  
  
 **專案名稱**  
 指定新專案的名稱。  副檔名為 .vcxproj 之類的專案檔將採用此名稱。  現有的程式碼檔則將保留其原始名稱。  
  
 **從這些資料夾將檔案加入專案**  
 當選取時，會設定讓精靈將現有的程式碼檔從原始的目錄 \(在這個控制項下方的清單方塊中指定\) 複製到新專案中。  
  
 **加入子資料夾**  
 指定從 \[**資料夾**\] 行所列目錄的所有子目錄，將程式碼檔複製到新專案中。  
  
 **資料夾**  
 表示目錄的路徑，其中包含要複製到新專案中的現有程式碼檔。  此行會列出讓精靈用以搜尋現有程式碼檔的所有目錄。  
  
 **加入**  
 顯示 \[**從這個資料夾將檔案加入專案中**\] 對話方塊，協助您指定精靈將用以搜尋現有程式碼檔的目錄。  
  
 **Remove**  
 刪除這個控制項左邊清單方塊中選取的目錄路徑。  
  
 **加入專案的檔案類型**  
 指定精靈將依據指定副檔名加入新專案中的檔案類型。  副檔名的前面會加上星號 \(\*\) 萬用字元，並在副檔名清單中以分號隔開。  
  
 **在方案總管中顯示所有檔案**  
 指定新專案中的所有檔案都能在 \[方案總管\] 視窗中看見並顯示。  這個選項預設為啟用。