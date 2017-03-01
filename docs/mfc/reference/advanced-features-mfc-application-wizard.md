---
title: "進階功能，MFC 應用程式精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.advanced
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
caps.latest.revision: 17
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ab9e67efc6fad90f2f9eb140411d063320f09feb
ms.lasthandoff: 02/24/2017

---
# <a name="advanced-features-mfc-application-wizard"></a>MFC 應用程式精靈、進階功能
本主題列出應用程式的其他功能選項，例如說明、列印支援等。 請在各章節中，指明這些進階功能的額外支援。  
  
 **即時線上說明 (HTML)**  
 會產生一組即時線上說明，請使用 F1 使用 [說明] 功能表中，或按一下說明檔案**協助**對話方塊上的按鈕。 必須有說明編譯器才能支援 [說明]。 如果沒有說明編譯器，可重新執行安裝程式進行安裝。  
  
 請參閱[HTML 說明︰ 程式的即時線上說明](../../mfc/html-help-context-sensitive-help-for-your-programs.md)和[說明檔案 （HTML 說明）](../../ide/help-files-html-help.md)如需詳細資訊。  
  
 **列印和預覽列印**  
 產生程式碼來處理列印、 列印設定和預覽列印命令，藉由呼叫成員函式[CView 類別](../../mfc/reference/cview-class.md)MFC 程式庫。 精靈也會將這些函式的命令加入應用程式的功能表中。 列印支援，僅適用於指定應用程式，**文件/檢視架構支援**中[MFC 應用程式精靈、 應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)精靈頁面。 在預設情況下，文件 / 檢視應用程式皆有列印支援。  
  
 **自動化**  
 指定應用程式可處理另一個應用程式中實作的物件，或將應用程式公開至 Automation 用戶端。  
  
 **ActiveX 控制項**  
 支援 ActiveX 控制項 (預設)。 如果您未選取此選項，而且稍後想要將 ActiveX 控制項插入您的專案，您必須加入呼叫[AfxEnableControlContainer](http://msdn.microsoft.com/library/7aa0b9d2-5329-4bc3-9d41-856e30fe2c2b)應用程式中[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)成員函式。  
  
 **MAPI (訊息 API)**  
 指定應用程式可建立、操作、傳輸和儲存郵件訊息。  
  
 **Windows 通訊端**  
 支援 Windows Sockets，您可以用來撰寫在 TCP/IP 網路上通訊的應用程式。  
  
 **使用中的協助工具**  
 新增支援[Cwnd](http://msdn.microsoft.com/library/windows/desktop/dd318466)至[CWnd](../../mfc/reference/cwnd-class.md)-衍生的類別，您可以使用自訂使用者介面協助工具用戶端更好的互動。  
  
 **通用控制項資訊清單**  
 預設為啟用。 產生應用程式資訊清單，以啟用 Microsoft Windows XP 和新作業系統中的通用控制項 DLL。  
  
 6.0 版的通用控制項 DLL 不會自動更新目前應用程式所使用的舊版通用控制項。 若要使用 6.0 版的通用控制項 DLL，您必須建立應用程式資訊清單，以引導應用程式載入此 DLL。 這個通用控制項 DLL 也支援 Windows XP 主題。  
  
 應用程式資訊清單也可以指定您的應用程式所需的其他 DLL 和版本。 如需應用程式資訊清單的詳細資訊，請參閱[隔離的應用程式和-並存組件](http://msdn.microsoft.com/library/dd408052)中[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
 **支援重新啟動管理員**  
 新增支援[Windows 重新啟動管理員](http://msdn.microsoft.com/library/windows/desktop/aa373680\(v=vs.85\).aspx)。 這段影片示範如何使用 MFC 的重新啟動管理員︰ [i︰ 如何使用新的重新啟動管理員](http://msdn.microsoft.com/vstudio/ee886407)。  
  
 **進階的框架窗格**  
 |選項|說明|  
|------------|-----------------|  
|**總管停駐窗格**|建立類似 Visual Studio 停駐窗格**方案總管 中**主框架視窗的左邊。|  
|**輸出停駐**|建立類似 Visual Studio 停駐窗格**輸出**主框架視窗底下的窗格。|  
|**屬性停駐窗格**|建立類似 Visual Studio 停駐窗格**屬性**主框架視窗右邊的窗格。|  
|**瀏覽窗格**|在主框架視窗左邊，建立類似 Outlook 巡覽列的停駐窗格。|  
|**標題列**|在主框架視窗上方建立 Office 樣式的標題列。|  
  
 **檔案清單中最近的檔案數目**  
 指定最近使用的檔案清單中列出的檔案數量。 預設值為 4。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)


