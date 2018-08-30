---
title: 如何： 建置隔離的應用程式以使用 COM 元件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b94a41aef1122a507a8966c475b9a87c69e3789
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196828"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>如何：建置隔離的應用程式以使用 COM 元件
隔離的應用程式是內建於程式資訊清單的應用程式。 您可以建立隔離的應用程式以使用 COM 元件。  
  
### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>加入 COM 參考，以隔離的應用程式資訊清單  
  
1.  開啟隔離的應用程式的專案屬性頁。  
  
2.  依序展開**組態屬性**節點，然後展開**資訊清單工具**節點。  
  
3.  選取 **隔離的 COM**屬性頁面中，然後再把**元件的檔案名稱**屬性設為您想要隔離的應用程式使用之 COM 元件的名稱。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
### <a name="to-build-manifests-into-isolated-applications"></a>若要在隔離的應用程式中建置資訊清單  
  
1.  開啟隔離的應用程式的專案屬性頁。  
  
2.  依序展開**組態屬性**節點，然後展開**資訊清單工具**節點。  
  
3.  選取 **輸入和輸出**屬性頁面中，然後再把**內嵌資訊清單**屬性等於**是**。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
5.  建置方案。  
  
## <a name="see-also"></a>另請參閱  
 [隔離的應用程式](/windows/desktop/SbsCs/isolated-applications)   
 [關於並排顯示的組件](/windows/desktop/SbsCs/about-side-by-side-assemblies-)