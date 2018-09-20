---
title: 複合文件支援，MFC 應用程式精靈 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.compdoc
dev_langs:
- C++
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fef6fd59166a0999221d420f58e0f329c780fd06
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416067"
---
# <a name="compound-document-support-mfc-application-wizard"></a>MFC 應用程式精靈、複合文件支援

在 MFC 應用程式精靈的此頁面上，指定何種層級應用程式會提供複合和作用中的文件支援。 您的應用程式必須支援文件/檢視架構支援複合文件和文件範本。

根據預設，應用程式會包含任何複合文件支援。 如果您接受此預設值時，您的應用程式無法支援主動式文件或複合檔案。

- **複合文件支援**

   判斷您的應用程式提供的容器支援、 伺服器支援，或兩者。 如需此區域的詳細資訊，請參閱：

   - [容器：實作容器](../../mfc/containers-implementing-a-container.md)

   - [伺服器：實作伺服器](../../mfc/servers-implementing-a-server.md)

   |選項|描述|
   |------------|-----------------|
   |**無**|表示物件連結與嵌入 (OLE) 不支援。 根據預設，應用程式精靈 建立不含 ActiveX 支援應用程式。|
   |**容器**|包含連結和內嵌的物件。|
   |**迷你伺服器**|表示應用程式可以建立和管理複合文件物件。 請注意，迷你伺服器無法執行獨立存在，而且只支援內嵌的項目。|
   |**完整伺服器**|表示應用程式可以建立和管理複合文件物件。 完整的伺服器可執行獨立和同時支援連結與內嵌項目。|
   |**容器/全功能伺服器**|指出應用程式可以同時為容器和伺服器。 容器是可以將內嵌或連結的項目併入本身的文件的應用程式。 可以建立使用的自動化項目由容器應用程式的應用程式伺服器。|

- **其他選項**

   指出您的應用程式是否支援主動式文件。 請參閱[主動式文件](../../mfc/active-documents.md)如需有關這項功能。

   |選項|描述|
   |------------|-----------------|
   |**作用中的文件伺服程式**|表示應用程式可以建立和管理使用中的文件。 如果您選取此選項時，您必須使用中文件伺服器的指定檔案延伸模組**副檔名**方塊中[文件樣板字串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)精靈頁面。 請參閱[現用文件伺服程式](../../mfc/active-document-servers.md)如需詳細資訊。|
   |**主動式文件容器**|指出應用程式可以包含其範圍內的主動式文件。 例如，作用中的文件可能包含 Internet Explorer 文件或 Office 文件，例如 Microsoft Word 檔案或 Excel 試算表。 請參閱[作用中的文件內含項目](../../mfc/active-document-containment.md)如需詳細資訊。|
   |**支援複合檔案**|不會序列化使用複合檔案格式的容器應用程式的文件。 這個選項會強制載入到記憶體中包含物件的整個檔案。 無法使用累加儲存個別物件。 如果一個物件已變更且隨後儲存時，會儲存在檔案中的所有物件。|

## <a name="see-also"></a>另請參閱

[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)

