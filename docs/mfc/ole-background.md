---
title: OLE 背景
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: baa2bca8b2e06fd55591c3a4fa2a9752abbb5355
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830783"
---
# <a name="ole-background"></a>OLE 背景

OLE 是一種機制，可讓使用者建立和編輯包含由多個應用程式所建立的項目或「物件」的文件。

> [!NOTE]
> OLE 最初是物件連結和嵌入的縮寫。 不過，它現在稱為 OLE。 OLE 與連結和內嵌無關的部分現在是 Active 技術的一部分。

OLE 文件 (以往稱為複合文件) 可完美整合各種類型的資料或元件。 音效短片、試算表和點陣圖是可在 OLE 文件中找到之元件的典型的例子。 在您的應用程式中支援 OLE 可讓您的使用者使用 OLE 文件，而不需要在不同的應用程式之間切換；OLE 會幫您作切換。

您可以使用一個容器應用程式來建立複合文件和一個伺服器應用程式或元件應用程式在容器文件內建立項目。 您撰寫的應用程式可以是容器、伺服器或兩者。

OLE 整合了許多不同的概念，其目標是要在應用程式之間進行完美的互動。 這些區域包含下列各項：

- 連結和內嵌

   連結和內嵌是儲存在由其他應用程式所建立 OLE 文件內建立之項目的兩種方法。 如需兩者之間差異的一般資訊，請參閱 [OLE 背景：連結和](ole-background-linking-and-embedding.md)內嵌一文。 如需詳細資訊，請參閱這些文章： [容器](containers.md) 和 [伺服器](servers.md)。

- 就地啟用 (視覺化編輯)

   在容器文件中啟用內嵌項目稱為就地啟用或視覺化編輯。 容器應用程式的介面會變更，以整合建立內嵌項目之元件應用程式的功能。 連結項目永遠不會就地啟用，因為實際的項目資料是包含在個別的檔案中，該檔案已超出包含這個連結的應用程式內容之外。 如需就地啟用的詳細資訊，請參閱 [啟用](activation-cpp.md)文章。

   > [!NOTE]
   > 連結和內嵌與就地啟用提供了 OLE 視覺化編輯的主要功能。

- 自動化自動化可讓一個應用程式驅動另一個應用程式。 驅動應用程式稱為 Automation 用戶端，而被驅動的應用程式稱為 Automation 伺服器或 Automation 元件。 如需自動化的詳細資訊，請參閱 [Automation 用戶端](automation-clients.md) 和 [automation 伺服器](automation-servers.md)文章。

   > [!NOTE]
   > Automation 可在 OLE 和 Active 技術內容中運作。 您可以自動化任何基於 COM 的物件。

- 複合檔案

   複合檔案提供的標準檔案格式簡化了 OLE 應用程式的複合文件結構化儲存。 在複合檔案內，儲存體具有許多目錄的功能，而資料流則具有許多檔案的功能。 這項技術也稱為結構化儲存體。 如需複合檔案的詳細資訊，請參閱「 [容器：複合檔案](containers-compound-files.md)」一文。

- 制式資料傳輸

   制式資料傳輸 (UDT) 是一組允許資料以標準方式傳送和接收的介面，不管實際上選擇的是哪一種傳送資料的方法。 UDT 是藉由拖放動作傳輸資料的基礎。 UDT 現在是現有 Windows 資料傳輸的基礎，例如剪貼簿和動態資料交換 (DDE)。 如需 UDT 的詳細資訊，請參閱 [ (OLE) 的資料物件和資料來源 ](data-objects-and-data-sources-ole.md)一文。

- 拖放

   拖放功能是一種容易使用、直接在應用程式之間、在應用程式的視窗之間，甚至是在應用程式的單一視窗中操作以傳輸資料的技術。 要傳送的資料會進行選取並拖曳至所需的目的地。 拖放動作會根據制式資料傳輸的方式進行。 如需拖放的詳細資訊，請參閱 [拖放](drag-and-drop-ole.md)文章。

- 元件物件模型

   元件物件模型 (COM) 提供了可在 OLE 物件彼此通訊時使用的基礎結構。 MFC OLE 類別為程式設計人員簡化了 COM。 COM 是 Active 技術的一部分，因為 COM 物件是 OLE 和 Active 技術的基礎。 如需 COM 的詳細資訊，請參閱 [Active Template Library (ATL) ](../atl/active-template-library-atl-concepts.md) 主題。

一些更重要的 OLE 主題會包含在下列文件中：

- [OLE 背景：連結和內嵌](ole-background-linking-and-embedding.md)

- [OLE 背景：容器和伺服器](ole-background-containers-and-servers.md)

- [OLE Background：執行策略](ole-background-implementation-strategies.md)

- [OLE 背景： MFC 實作為](ole-background-mfc-implementation.md)

如需在上述文章中找不到的一般 OLE 資訊，請搜尋 Microsoft Docs 中 [的 ole](/search/?terms=ole) 。

## <a name="see-also"></a>另請參閱

[OLE](ole-in-mfc.md)
