---
title: "COleLinkingDoc Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleLinkingDoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleLinkingDoc class"
  - "OLE containers, client items"
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleLinkingDoc Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援連結與內嵌項目的 OLE 容器文件的基底類別及內容。  
  
## 語法  
  
```  
class COleLinkingDoc : public COleDocument  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleLinkingDoc::COleLinkingDoc](../Topic/COleLinkingDoc::COleLinkingDoc.md)|建構 `COleLinkingDoc` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleLinkingDoc::Register](../Topic/COleLinkingDoc::Register.md)|註冊具有 OLE 系統 DLL 的文件。|  
|[COleLinkingDoc::Revoke](../Topic/COleLinkingDoc::Revoke.md)|移除文件的註冊。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[COleLinkingDoc::OnFindEmbeddedItem](../Topic/COleLinkingDoc::OnFindEmbeddedItem.md)|尋找指定的內嵌項目。|  
|[COleLinkingDoc::OnGetLinkedItem](../Topic/COleLinkingDoc::OnGetLinkedItem.md)|尋找指定之連接的項目。|  
  
## 備註  
 支援連結與內嵌項目稱為「連結容器的容器應用程式」。[OCLIENT](../../top/visual-cpp-samples.md) 範例應用程式是連結容器的範例。  
  
 當連結之項目的來源是在另一份文件中的內嵌項目，必須載入這個所包含的檔案才能編輯內嵌項目。  因此，在中，當使用者想要編輯連結之項目的來源時，連結容器必須能夠由另一個容器應用程式啟動。  您的應用程式也必須使用 [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) 類別，以建立文件，同時啟動的方式。  
  
 若要將您的容器連結容器，從 `COleLinkingDoc` 衍生您的文件類別而不是 [COleDocument](../../mfc/reference/coledocument-class.md)。  與其他 OLE 容器，您必須自行設計儲存應用程式的原生資料和內嵌或連結的項目類別。  此外，您也必須設計儲存您的原生資料結構。  如果您定義 `CDocItem`\-應用程式的原生資料 \(Native Data\) 的衍生類別，您可以使用 `COleDocument` 定義介面儲存原生資料以及您可用的資料。  
  
 若要讓您的應用程式都是由其他容器所啟動的方式，請宣告 `COleTemplateServer` 物件做為應用程式的 `CWinApp`成員的衍生類別:  
  
 [!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/CPP/colelinkingdoc-class_1.h)]  
  
 在您的 `CWinApp`的 `InitInstance` 成員函式的衍生類別，建立文件範本並指定您的 `COleLinkingDoc`衍生類別，文件類別:  
  
 [!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/CPP/colelinkingdoc-class_2.cpp)]  
  
 藉由呼叫物件的 `ConnectTemplate` 成員函式連接至您的文件範本的 `COleTemplateServer` 物件，並呼叫 **COleTemplateServer::RegisterAll**註冊具有 OLE 系統中所有類別的物件:  
  
 [!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/CPP/colelinkingdoc-class_3.cpp)]  
  
 如需範例 `CWinApp`衍生類別定義和 `InitInstance` 生效，請參閱 OCLIENT.H 和 OCLIENT.CPP 在 MFC 範例 [OCLIENT](../../top/visual-cpp-samples.md)。  
  
 如需使用 `COleLinkingDoc`的相關資訊，請參閱 Microsoft 知識庫文件 [容器:實作容器](../../mfc/containers-implementing-a-container.md) 和 [容器:進階功能](../../mfc/containers-advanced-features.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 `COleLinkingDoc`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC 範例 OCLIENT](../../top/visual-cpp-samples.md)   
 [COleDocument Class](../../mfc/reference/coledocument-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)