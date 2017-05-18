---
title: "預設的 ATL 專案組態 |Microsoft 文件"
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
- ATL projects, default configurations
ms.assetid: 7e272722-41af-4330-b965-a6d74ec16880
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 41ab65c411bef478d063e5165d3167f58ace37d7
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="default-atl-project-configurations"></a>預設的 ATL 專案組態
這個主題會比較的預設 ATL 專案組態 Visual c + +.NET 中使用 Visual c + + 6.0 中的預設專案組態。  
  
## <a name="visual-c-net-default-configurations"></a>Visual c + +.NET 的預設組態  
 在 Visual c + +.NET 中，ATL 專案精靈 會依預設，建立兩個專案組態。  
  
### <a name="visual-c-net-configurations"></a>Visual c + +.NET 組態  
  
|組態|字元集|ATL 用途|  
|-------------------|-------------------|----------------|  
|發行|MBCS|DLL|  
|偵錯|MBCS|DLL|  
  
 **字元集**， **ATL 用法**，都可以變更在**專案設定**下的對話方塊**一般** 索引標籤。 您也可以加入自己使用組態管理員的組態。 如需詳細資訊，請參閱[組建組態](/visualstudio/ide/understanding-build-configurations)。  
  
## <a name="version-60-default-configurations"></a>6.0 版的預設組態  
 Visual c + + 6.0 版 （現在稱為 ATL 專案精靈） 的 ATL COM AppWizard 會依預設建立六個專案組態。 設定已發行、 偵錯、 Unicode 和使用 CRT、 ATL 設定變化。 如果您想要可以在 Visual c + +.NET 中使用組態管理員中，複製所有的組態。  
  
### <a name="version-60-configurations"></a>6.0 版的組態  
  
|組態|字元集|ATL 用途|  
|-------------------|-------------------|----------------|  
|偵錯|MBCS|Static|  
|偵錯 Unicode|UNICODE|Static|  
|發行最小相依性|MBCS|Static|  
|發行最小相依性 Unicode|UNICODE|Static|  
|發行最小大小|MBCS|DLL|  
|發行最小大小 Unicode|UNICODE|DLL|  
  
## <a name="see-also"></a>另請參閱  
 [使用 ATL 和 C 執行階段程式碼的程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [使用專案屬性](../../ide/working-with-project-properties.md)   
 [組態管理員對話方塊](http://msdn.microsoft.com/en-us/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [編譯和建置](/visualstudio/ide/compiling-and-building-in-visual-studio)


