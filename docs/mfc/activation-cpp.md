---
title: "啟用 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 70017721fb59fa0c6d18d568546d9618257328b5
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="activation-c"></a>啟用 (C++)
本文說明的角色啟用視覺化編輯 OLE 項目。 使用者已在容器文件中內嵌 OLE 項目之後，它可能需要使用。 若要這樣做，使用者按兩下項目，該項目就會啟動。 編輯啟用最常見的活動。 許多目前 OLE 項目，當啟動進行編輯，會導致目前的框架視窗變更以反映這些屬於伺服器應用程式建立項目的功能表和工具列。 此行為，已知為就地啟用，可讓使用者編輯複合文件中的任何內嵌項目，而不需離開容器文件視窗。  
  
 它也可編輯個別視窗中的內嵌的 OLE 項目。 容器或伺服器應用程式不支援就地啟用時，會發生此項目。 在此情況下，當使用者按兩下內嵌項目時，伺服器應用程式會在個別視窗中啟動和內嵌的項目會顯示為自己文件。 使用者可編輯此視窗中的項目。 當編輯完成時，使用者關閉伺服器應用程式，並傳回該容器應用程式。  
  
 或者，使用者可以選擇 「 開啟編輯 」 與**\<物件 > 開啟**命令**編輯**功能表。 這是在個別視窗中開啟物件。  
  
> [!NOTE]
>  編輯個別視窗中內嵌的項目所 OLE，第 1 版中的標準行為，有些 OLE 應用程式可能支援此樣式的編輯。  
  
 就地啟用升級文件為中心的方法來建立文件。 使用者可以將複合文件視為單一實體，此作業不需要應用程式之間切換。 不過，在就地啟用只適用於內嵌的項目，不會針對連結的項目： 必須在個別視窗中進行編輯。 這是因為連結的項目實際上儲存在不同的位置。 編輯連結的項目會儲存資料的資料，也就是實際的內容中進行。 編輯連結的項目，個別視窗中會提醒使用者資料屬於另一個文件。  
  
 MFC 不支援巢狀的就地啟用。 如果您建立容器/伺服器應用程式，且容器/伺服器內嵌在另一個容器和就地啟用，它無法就地啟動內嵌在它之內的物件。  
  
 當使用者按兩下它，在內嵌項目會發生什麼事取決於定義項目的動詞命令。 如需資訊，請參閱[啟用： 動詞命令](../mfc/activation-verbs.md)。  
  
## <a name="see-also"></a>另請參閱  
 [OLE](../mfc/ole-in-mfc.md)   
 [容器](../mfc/containers.md)   
 [伺服器](../mfc/servers.md)

