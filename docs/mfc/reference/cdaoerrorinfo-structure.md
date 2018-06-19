---
title: CDaoErrorInfo 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c11ebaa7d315d09cea40b4ddc94d5afff498bf7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366625"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo 結構
`CDaoErrorInfo`結構包含的資料存取物件 (DAO) 定義的物件時發生錯誤的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CDaoErrorInfo  
{  
    long m_lErrorCode;  
    CString m_strSource;  
    CString m_strDescription;  
    CString m_strHelpFile;  
    long m_lHelpContext;  
};  
```  
  
#### <a name="parameters"></a>參數  
 *m_lErrorCode*  
 數字的 DAO 錯誤代碼。 請參閱 「 可截獲資料存取錯誤 」 DAO [說明] 中的主題。  
  
 *m_strSource*  
 物件或最初產生錯誤的應用程式的名稱。 來源屬性的指定字串運算式，最初產生錯誤; 表示的物件運算式通常是物件的類別名稱。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 來源屬性 」。  
  
 *m_strDescription*  
 與錯誤相關聯的描述性字串。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 描述屬性 」。  
  
 *m_strHelpFile*  
 Microsoft Windows 說明檔案的完整的路徑。 如需詳細資訊，請參閱 DAO 說明主題 「 HelpContext HelpFile 屬性 」。  
  
 *m_lHelpContext*  
 Microsoft Windows 說明檔主題的內容識別碼。 如需詳細資訊，請參閱 DAO 說明主題 「 HelpContext HelpFile 屬性 」。  
  
## <a name="remarks"></a>備註  
 MFC 不會封裝 DAO 類別中的錯誤物件。 相反地， [CDaoException](../../mfc/reference/cdaoexception-class.md)類別提供的介面來存取在 DAO 中所包含的錯誤集合**資料庫引擎**物件，也包含 所有工作區的物件。 MFC DAO 作業會擲回`CDaoException`物件，您攔截，MFC 會填入`CDaoErrorInfo`結構，並將它儲存在例外狀況物件的[m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo)成員。 (如果您選擇直接呼叫 DAO，您必須呼叫例外狀況物件的[GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo)成員函式自行填滿`m_pErrorInfo`。)  
  
 如需處理 DAO 錯誤的詳細資訊，請參閱文章[例外狀況： 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。 如需相關資訊，請參閱主題 DAO [說明] 中的 「 錯誤物件 」。  
  
 所擷取的資訊[CDaoException::GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo)成員函式會儲存在`CDaoErrorInfo`結構。 檢查[m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo)資料成員從`CDaoException`您攔截例外狀況處理常式或呼叫中的物件`GetErrorInfo`從`CDaoException`以檢查錯誤，可能需要明確建立的物件直接呼叫 DAO 介面期間發生。 `CDaoErrorInfo` 也會定義`Dump`成員函式在偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoErrorInfo`物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
