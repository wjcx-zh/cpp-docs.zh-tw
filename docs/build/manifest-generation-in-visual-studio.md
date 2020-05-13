---
title: 在 Visual Studio 中產生資訊清單
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: f055e3d16dfc0ea4320883210458ae10daebdc45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273352"
---
# <a name="manifest-generation-in-visual-studio"></a>在 Visual Studio 中產生資訊清單

您可以在 [專案**屬性頁**] 對話方塊中，控制特定專案的資訊清單檔的產生。 **在 [設定**內容] 索引標籤上，依序按一下 [**連結器**] 和 [**資訊清單**檔案] **，然後** 根據預設，新專案的專案屬性會設定為產生資訊清單檔案。 不過，您可以使用專案的 [**產生資訊清單**] 屬性來停用專案的資訊清單產生。 當這個屬性設定為 **[是]** 時，就會產生此專案的資訊清單。 否則，連結器會在解析應用程式代碼的相依性時忽略元件資訊，而不會產生資訊清單。

Visual Studio 中的組建系統可讓資訊清單內嵌在最終二進位應用程式檔中，或產生為外部檔案。 這個行為是由 [**專案屬性**] 對話方塊中的 [**內嵌資訊清單**] 選項所控制。 若要設定此屬性，請開啟 [**資訊清單工具**] 節點，然後選取 [**輸入和輸出**]。 如果資訊清單不是內嵌的，則會產生為外部檔案，並儲存在與最後二進位檔相同的目錄中。 如果資訊清單是內嵌的，Visual Studio 會使用下列程式來內嵌最後的資訊清單：

1. 將原始程式碼編譯成物件檔案之後，連結器會收集相依元件資訊。 連結最後的二進位檔時，連結器會產生一個中繼資訊清單，供稍後用來產生最後的資訊清單。

1. 在中繼資訊清單和連結完成之後，將會執行資訊清單工具來合併最後的資訊清單，並將其儲存為外部檔案。

1. 專案組建系統接著會偵測資訊清單工具所產生的資訊清單是否包含與已內嵌于二進位檔中的資訊清單不同的資訊。

1. 如果在二進位檔中內嵌的資訊清單與資訊清單工具所產生的資訊清單不同，或二進位檔不包含內嵌的資訊清單，Visual Studio 將會再叫用連結器一次，將外部資訊清單檔內嵌為資源。

1. 如果內嵌在二進位檔中的資訊清單與資訊清單工具所產生的資訊清單相同，則組建會繼續進行下一個組建步驟。

資訊清單是以文字資源的形式內嵌在最後一個二進位檔中，而且可以藉由在 Visual Studio 中開啟最後一個二進位檔做為檔案來加以查看。 若要確保資訊清單指向正確的程式庫，請遵循[瞭解 Visual C++ 應用程式的](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md)相依性中所述的步驟，或遵循[疑難排解](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)一節中所述的建議。

## <a name="see-also"></a>請參閱

[瞭解 C/c + + 程式的資訊清單產生](understanding-manifest-generation-for-c-cpp-programs.md)
