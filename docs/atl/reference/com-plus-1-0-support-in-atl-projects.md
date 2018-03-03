---
title: "COM + 1.0 支援 ATL 專案中 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.MTS
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3b55cb078dc5db1f0bf727a10f2a77ebfddd260
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="com-10-support-in-atl-projects"></a>COM + 1.0 支援在 ATL 專案
您可以使用[ATL 專案精靈](../../atl/reference/creating-an-atl-project.md)建立專案與 COM + 1.0 元件的基本支援。  
  
 COM + 1.0 被設計來開發分散式的元件為基礎的應用程式。 它也會提供部署及管理這些應用程式的執行階段基礎結構。  
  
 如果您選取**支援 COM + 1.0**核取方塊，精靈會修改建置指令碼在連結步驟。 具體來說，COM + 1.0 專案會連結至下列的程式庫：  
  
-   comsvcs.lib  
  
-   Mtxguid.lib  
  
 如果您選取**支援 COM + 1.0**核取方塊，您也可以選取**支援元件登錄器**。 元件的註冊機構可讓您取得元件的清單、 登錄元件，或取消登錄元件 （個別或全部） 的 COM + 1.0 物件。  
  
## <a name="see-also"></a>請參閱  
 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)   
 [ATL 和 C 執行階段程式碼的程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)

