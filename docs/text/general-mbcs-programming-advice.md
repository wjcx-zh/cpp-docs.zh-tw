---
title: "一般 MBCS 程式設計的建議 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b379c163963a9ae0dd0c59c7d0fc809fee4f46d0
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="general-mbcs-programming-advice"></a>一般 MBCS 程式設計的建議
使用下列秘訣：  
  
-   為彈性，請使用執行階段巨集例如`_tcschr`和`_tcscpy`盡可能。 如需詳細資訊，請參閱[Tchar.h 中的泛用文字對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
-   使用 C 執行階段`_getmbcp`函式可取得目前的字碼頁的相關資訊。  
  
-   請勿重複使用字串資源。 目標語言中，根據給定的字串可能會有不同的意義轉譯時。 例如，「 檔案 」，在應用程式的主功能表可能會有不同的轉譯在對話方塊中的 「 檔案 」 的字串。 如果您需要使用具有相同名稱的多個字串，請針對每個使用不同的字串識別碼。  
  
-   您可能想要了解是否已啟用 MBCS 的作業系統上執行應用程式。 若要這樣做，請在程式啟動; 設定旗標請勿依賴 API 呼叫。  
  
-   在設計對話方塊時，允許大約 30%結尾的 MBCS 轉譯為靜態文字控制項的額外空間。  
  
-   時請小心選取字型，您的應用程式，因為有些字型並不適用於所有系統。  
  
-   當選取的字型對話方塊時，使用[MS Shell Dlg](http://msdn.microsoft.com/library/windows/desktop/dd374112)而不是新細明體或新細明體。 MS Shell Dlg 會取代正確的字型，由系統建立對話方塊之前。 使用 MS Shell Dlg，可確保作業系統來處理這種字型中的任何變更會自動使用。 （MFC 取代 MS Shell Dlg DEFAULT_GUI_FONT 或 Windows 95、 Windows 98 和 Windows NT 4 上的系統字型因為這些系統未正確處理 MS Shell Dlg。）  
  
-   在設計您的應用程式時，決定可當地語系化的字串。 如果在不確定，請假設任何給定的字串將會進行當地語系化。 因此，請勿與無法混合可當地語系化的字串。  
  
## <a name="see-also"></a>請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [增量和遞減指標](../text/incrementing-and-decrementing-pointers.md)