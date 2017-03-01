---
title: "連結器工具錯誤 LNK2005 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4ac033535632e94a365aa8dafd849f2ab28a3af7
ms.openlocfilehash: bf93f364b3dc7156a62eb1c474177eb7b85c7827
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2005"></a>連結器工具錯誤 LNK2005
符號已定義於物件   
  
以其裝飾形式顯示的 `symbol` 已定義多次。  
  
如需詳細資訊，請參閱知識庫文件：  
  
-   [在 Visual c + + 中正確的順序連結的 CRT 程式庫和 MFC 程式庫時，就會發生 LNK2005 錯誤](https://support.microsoft.com/kb/148652)  
  
-   [修正︰ 全域多載的刪除運算子原因發生 LNK2005](https://support.microsoft.com/kb/140440)  
  
-   [當您編譯 Visual c + + ATL 可執行檔 (.exe) 專案時，您會收到發生 LNK2005 錯誤](https://support.microsoft.com/kb/184235)。  
  
此錯誤後面是嚴重錯誤[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  也使用時，混合靜態和動態程式庫[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
2.  符號是封裝函式 (由使用編譯[/Gy](../../build/reference/gy-enable-function-level-linking.md))，包含多個檔案中，但編譯之間不同。 重新編譯包含 `symbol` 的所有檔案。  
  
3.  符號在不同程式庫的兩個成員物件中定義不同，而這兩個成員物件都已被使用。  
  
4.  絕對被定義了兩次，每一個定義具有不同的值。  
  
5.  標頭檔宣告並定義變數。 可能的解決方案包括：  
  
    -   在 .h 中宣告變數：`extern BOOL MyBool;`，然後在 .c 或 .cpp 檔案中指派給它：`BOOL MyBool = FALSE;`。  
  
    -   宣告變數[靜態](../../cpp/storage-classes-cpp.md#static)。  
  
    -   宣告變數[selectany](../../cpp/selectany.md)。  
  
6.  如果您將 uuid.lib 與其他定義 GUID 的 .lib 檔 (例如 oledb.lib 和 adsiid.lib) 結合使用。 例如：  
  
    ```  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     若要修正問題，請新增[/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md)加入連結器命令列選項，並確保 uuid.lib 是最先參考的程式庫。
