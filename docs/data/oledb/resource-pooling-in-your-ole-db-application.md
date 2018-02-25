---
title: "OLE DB 應用程式的資源集中化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 84b8814974850238ccf0be7411821d6e2cce8880
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="resource-pooling-in-your-ole-db-application"></a>OLE DB 應用程式的資源集中化
若要充分利用在您的應用程式集區，您必須確定取得透過資料來源的 OLE DB 服務會叫用**IDataInitialize**或**IDBPromptInitialize**。 如果您直接使用`CoCreateInstance`要叫用提供者的 CLSID 為基礎的提供者，沒有 OLE DB 服務會叫用。  
  
 OLE DB 服務維護連接的資料來源只要參考的集區**IDataInitialize**或**IDBPromptInitialize**保留或只要沒有使用中的連接。 集區也會在 COM + 1.0 服務或 Internet Information Services (IIS) 的環境中自動維護。 如果您的應用程式會利用共用 COM + 1.0 服務或 IIS 環境之外，您應該保留的參考**IDataInitialize**或**IDBPromptInitialize**或保留至少一個連接。 若要確定，集區不會不取得終結應用程式所發行最後一次連接時，保留參考，或保存您的應用程式的存留期的連接。  
  
 OLE DB 服務識別時從中繪製連接集區的`Initialize`呼叫。 連接取自集區之後，它無法移至不同的集區。 因此，避免發生動作，在您的應用程式中變更初始化資訊，例如呼叫`UnInitialize`或呼叫`QueryInterface`特定提供者介面，然後再呼叫`Initialize`。 此外，建立具有提示的值以外的連接**DBPROMPT_NOPROMPT**未共用。 不過，擷取透過提示所建立的連線初始化字串可以用來建立其他共用相同的資料來源連接。  
  
 某些提供者必須建立個別的連線，每個工作階段。 如果有的話，這些其他的連接，必須分別編列在分散式交易中。 OLE DB 服務快取並重複使用的每個資料來源的單一工作階段，但如果應用程式會要求一次的多個工作階段，從單一資料來源，提供者最後可能會建立額外的連接，以及執行的是其他交易登記不共用。 會比從單一資料來源建立多個工作階段管理的集區環境中建立個別的資料來源的每個工作階段實際更有效率。  
  
 最後，因為 ADO 會自動將使用的 OLE DB 服務，您可以使用 ADO 來建立連接，且共用及登記會自動進行。  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 資源共用和服務](../../data/oledb/ole-db-resource-pooling-and-services.md)