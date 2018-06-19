---
title: 如何： 建置隔離的應用程式以使用 COM 元件 |Microsoft 文件
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
ms.openlocfilehash: 2ed2f43721eb698552ccde3e1b51ed4d6e467179
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367881"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>如何：建置隔離的應用程式以使用 COM 元件
隔離的應用程式是內建於程式資訊清單的應用程式。 您可以建立隔離的應用程式使用 COM 元件。  
  
### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>若要加入的 隔離的應用程式資訊清單中的 COM 參考  
  
1.  開啟 隔離的應用程式的專案屬性頁。  
  
2.  展開**組態屬性** 節點，然後展開**資訊清單工具**節點。  
  
3.  選取**隔離的 COM**屬性頁上，並將其設定**元件檔名**屬性設為您想要隔離的應用程式使用之 COM 元件的名稱。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
### <a name="to-build-manifests-into-isolated-applications"></a>若要建置到隔離的應用程式資訊清單  
  
1.  開啟 隔離的應用程式的專案屬性頁。  
  
2.  展開**組態屬性** 節點，然後展開**資訊清單工具**節點。  
  
3.  選取**輸入和輸出**屬性頁上，並將其設定**內嵌資訊清單**屬性等於**是**。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
5.  建置方案。  
  
## <a name="see-also"></a>另請參閱  
 [隔離的應用程式](http://msdn.microsoft.com/library/aa375190)   
 [關於-並存組件](http://msdn.microsoft.com/library/ff951640)