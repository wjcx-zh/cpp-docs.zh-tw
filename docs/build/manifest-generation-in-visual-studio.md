---
title: 在 Visual Studio 中產生資訊清單
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: f055e3d16dfc0ea4320883210458ae10daebdc45
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781675"
---
# <a name="manifest-generation-in-visual-studio"></a>在 Visual Studio 中產生資訊清單

在專案中可控制特定專案產生的資訊清單檔**屬性頁**對話方塊。 在 **組態屬性**索引標籤上，按一下**連結器**，然後**資訊清單檔案**，然後**產生資訊清單**。 根據預設新專案的專案屬性會設定為產生資訊清單檔案。 不過就可以停用產生資訊清單的專案，使用**產生資訊清單**專案屬性。 當這個屬性設定為**是**，就會產生此專案的資訊清單。 否則，連結器會忽略組件資訊時解析相依性的應用程式的程式碼，並不會產生資訊清單。

在 Visual Studio 中的建置系統可讓要內嵌於最終二進位的應用程式檔案，或做為外部檔案產生的資訊清單。 此行為受到**內嵌資訊清單**選項**專案屬性**對話方塊。 若要設定這個屬性，開啟**資訊清單工具**節點，然後選取**輸入和輸出**。 如果沒有內嵌資訊清單，則會產生做為外部檔案，並儲存在與最終二進位檔相同的目錄。 如果內嵌資訊清單中，Visual Studio 會將內嵌使用下列程序的最後一個資訊清單：

1. 將物件檔編譯的原始程式碼後，連結器會收集相依組件資訊。 當連結最終二進位檔，連結器會產生稍後用來產生最終的資訊清單的中繼資訊清單。

1. 中繼資訊清單和連結都完成之後，資訊清單工具將會執行合併的最後一個資訊清單，並將它儲存為外部檔案。

1. 專案建置系統會偵測到資訊清單工具所產生的資訊清單是否包含已內嵌於二進位檔的資訊清單的不同資訊。

1. 如果內嵌於二進位檔的資訊清單是不同的資訊清單的工具，所產生的資訊清單或二進位檔不包含內嵌的資訊清單，Visual Studio 將會叫用連結器一次內嵌於二進位檔做為外部的資訊清單檔案資源。

1. 如果資訊清單工具所產生的資訊清單相同的二進位檔中內嵌的資訊清單，建置會繼續至下一個建置步驟。

資訊清單內嵌於最終二進位檔為文字資源，就可以檢視為 Visual Studio 中的檔案開啟最終二進位檔。 若要確保資訊清單會指向正確的程式庫，請依照下列所述的步驟[了解的相依性視覺效果C++應用程式](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md)，或依照所述的建議[疑難排解](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)一節。

## <a name="see-also"></a>另請參閱

[了解 C/C++ 程式的資訊清單產生過程](understanding-manifest-generation-for-c-cpp-programs.md)
