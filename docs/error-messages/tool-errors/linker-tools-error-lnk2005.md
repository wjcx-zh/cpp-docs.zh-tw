---
title: "連結器工具錯誤 LNK2005 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2005"
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# 連結器工具錯誤 LNK2005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

符號已定義於物件  
  
 以其裝飾形式顯示的 `symbol` 已定義多次。  
  
 如需詳細資訊，請參閱知識庫文件：  
  
-   \<連結 C 執行階段程式庫在 MFC 程式庫之前連結時，發生 LNK2005 錯誤\> \(Q148652\)  
  
-   \<全域多載刪除運算子導致 LNK2005\> \(Q140440\)  
  
-   \<定義 \_ATL\_MIN\_CRT 時，新建及刪除發生 LNK2005 錯誤\> \(Q184235\)。  
  
 您可以在 MSDN Library CD\-ROM 或是在 [http:\/\/support.microsoft.com\/search](http://support.microsoft.com/search) 找到知識庫文件。  
  
 此錯誤後面是嚴重錯誤 [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。  
  
### 透過檢查下列可能原因進行修正  
  
1.  在同時使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 時，混合靜態和動態程式庫。  
  
2.  符號是封裝函式 \(透過使用 [\/Gy](../../build/reference/gy-enable-function-level-linking.md) 編譯而建立\)，包含在多個檔案中，但每個編譯之間不同。  重新編譯包含 `symbol` 的所有檔案。  
  
3.  符號在不同程式庫的兩個成員物件中定義不同，而這兩個成員物件都已被使用。  
  
4.  絕對被定義了兩次，每一個定義具有不同的值。  
  
5.  標頭檔宣告並定義變數。  可能的解決方案包括：  
  
    -   在 .h 中宣告變數：`extern BOOL MyBool;`，然後在 .c 或 .cpp 檔案中指派給它：`BOOL MyBool = FALSE;`。  
  
    -   宣告變數 [static](../../misc/static-cpp.md)。  
  
    -   宣告變數 [selectany](../../cpp/selectany.md)。  
  
6.  如果您將 uuid.lib 與其他定義 GUID 的 .lib 檔 \(例如 oledb.lib 和 adsiid.lib\) 結合使用。  例如：  
  
    ```  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     若要修正，請將 [\/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) 加入連結器命令列選項，並確保 uuid.lib 是最先參考的程式庫。