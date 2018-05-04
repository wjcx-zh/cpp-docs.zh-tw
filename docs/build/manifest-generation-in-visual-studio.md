---
title: 在 Visual Studio 產生資訊清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73b5cbe631d078dd6ee27b4f7e0a97503c36638b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="manifest-generation-in-visual-studio"></a>在 Visual Studio 中產生資訊清單
產生資訊清單檔案的特定專案可以在專案中控制**屬性頁**對話方塊。 在**組態屬性**索引標籤上，按一下 **連結器**，然後**資訊清單檔案**，然後**產生資訊清單**。 根據預設新專案的專案屬性會設定為產生資訊清單檔案。 不過它可能是停用產生資訊清單的專案使用**產生資訊清單**專案的屬性。 當這個屬性設定為**是**，在產生此專案的資訊清單。 否則，連結器時，會忽略組件資訊解決相依性的應用程式程式碼，並不會產生資訊清單。  
  
 在 Visual Studio 中的建置系統，可讓要內嵌於最終的二進位應用程式檔案，或做為外部檔案產生的資訊清單。 此行為由**內嵌資訊清單**選項**專案屬性**對話方塊。 若要設定這個屬性，開啟**資訊清單工具** 節點，然後選取**輸入和輸出**。 如果沒有內嵌資訊清單，則會產生做為外部檔案，並儲存在最終的二進位檔的相同目錄中。 如果內嵌資訊清單中，Visual Studio 會內嵌使用下列程序的最後一個資訊清單：  
  
1.  原始碼在編譯物件檔案後，連結器會收集相依組件資訊。 當將最終的二進位檔的連結，連結器會產生稍後用來產生最後的資訊清單的中繼資訊清單。  
  
2.  中繼資訊清單和連結都完成後，資訊清單工具將會執行合併最終的資訊清單，並將它儲存為外部檔案。  
  
3.  專案建置系統，會偵測到資訊清單工具所產生資訊清單是否包含已內嵌於二進位檔的資訊清單的不同資訊。  
  
4.  如果不同於資訊清單工具產生的資訊清單內嵌於二進位檔的資訊清單或二進位檔不包含內嵌的資訊清單，Visual Studio 會叫用連結器一次將內嵌於二進位檔做為外部的資訊清單檔案資源。  
  
5.  如果內嵌於二進位檔的資訊清單中都相同，資訊清單工具所產生資訊清單，組建會繼續到下一個建置步驟。  
  
 資訊清單內嵌於最終的二進位檔為文字資源，就可以檢視最終的二進位檔開啟為 Visual Studio 中的檔案。 若要確保資訊清單會指向正確的程式庫，請依照下列所述的步驟[了解 Visual c + + 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)或遵循所述的建議[疑難排解](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) > 一節。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 嵌入 C/c + + 應用程式資訊清單](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)   
 [關於私用組件](http://msdn.microsoft.com/library/ff951638)   
 [資訊清單工具](http://msdn.microsoft.com/library/aa375649)   
 [了解 C/C++ 程式的資訊清單產生過程](../build/understanding-manifest-generation-for-c-cpp-programs.md)