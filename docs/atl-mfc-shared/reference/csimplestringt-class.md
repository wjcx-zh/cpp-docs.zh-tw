---
title: "CSimpleStringT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CSimpleStringT"
  - "ATL::CSimpleStringT"
  - "ATL::CSimpleStringT<BaseType>"
  - "ATL.CSimpleStringT<BaseType>"
  - "CSimpleStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleStringT class"
  - "shared classes, CSimpleStringT"
  - "字串 [C++], ATL 類別"
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CSimpleStringT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示 `CSimpleStringT` 物件。  
  
## 語法  
  
```  
  
      template <typename   
      BaseType  
      >  
class CSimpleStringT  
```  
  
#### 參數  
 `BaseType`  
 字串類別的配置類型。  可以是下列其中一項：  
  
-   `char` \(ANSI 字串\)。  
  
-   `wchar_t` \(Unicode 字串\)。  
  
-   **TCHAR** \(適用於 ANSI 和 Unicode 字串\)。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleStringT::PCXSTR](../Topic/CSimpleStringT::PCXSTR.md)|使用常數字串的指標。|  
|[CSimpleStringT::PXSTR](../Topic/CSimpleStringT::PXSTR.md)|字串的指標。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleStringT::CSimpleStringT](../Topic/CSimpleStringT::CSimpleStringT.md)|建構 `CSimpleStringT` 物件以各種方式。|  
|[CSimpleStringT::~CSimpleStringT](../Topic/CSimpleStringT::~CSimpleStringT.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleStringT::Append](../Topic/CSimpleStringT::Append.md)|附加至現有的 `CSimpleStringT` 物件的 `CSimpleStringT` 物件。|  
|[CSimpleStringT::AppendChar](../Topic/CSimpleStringT::AppendChar.md)|將字元附加至現有的 `CSimpleStringT` 物件。|  
|[CSimpleStringT::CopyChars](../Topic/CSimpleStringT::CopyChars.md)|要複製的字元至另一個字串。|  
|[CSimpleStringT::CopyCharsOverlapped](../Topic/CSimpleStringT::CopyCharsOverlapped.md)|複製字元的緩衝區重疊的另一個字串。|  
|[CSimpleStringT::Empty](../Topic/CSimpleStringT::Empty.md)|強制字串長度為零。|  
|[CSimpleStringT::FreeExtra](../Topic/CSimpleStringT::FreeExtra.md)|釋放先前配置字串物件的任何額外的記憶體。|  
|[CSimpleStringT::GetAllocLength](../Topic/CSimpleStringT::GetAllocLength.md)|擷取物件的 `CSimpleStringT` 配置的長度。|  
|[CSimpleStringT::GetAt](../Topic/CSimpleStringT::GetAt.md)|傳回在指定的字元位置。|  
|[CSimpleStringT::GetBuffer](../Topic/CSimpleStringT::GetBuffer.md)|傳回指向儲存在 `CSimpleStringT`的字元。|  
|[CSimpleStringT::GetBufferSetLength](../Topic/CSimpleStringT::GetBufferSetLength.md)|傳回指向儲存在 `CSimpleStringT`的字元，會截斷為指定之長度。|  
|[CSimpleStringT::GetLength](../Topic/CSimpleStringT::GetLength.md)|傳回的字元數。 `CSimpleStringT` 物件的。|  
|[CSimpleStringT::GetManager](../Topic/CSimpleStringT::GetManager.md)|擷取 `CSimpleStringT` 物件的記憶體管理員。|  
|[CSimpleStringT::GetString](../Topic/CSimpleStringT::GetString.md)|擷取字串|  
|[CSimpleStringT::IsEmpty](../Topic/CSimpleStringT::IsEmpty.md)|測試 `CSimpleStringT` 物件不包含字元。|  
|[CSimpleStringT::LockBuffer](../Topic/CSimpleStringT::LockBuffer.md)|停用參考次數並防止緩衝區中的字串。|  
|[CSimpleStringT::Preallocate](../Topic/CSimpleStringT::Preallocate.md)|配置字元緩衝區的指定數目的記憶體。|  
|[CSimpleStringT::ReleaseBuffer](../Topic/CSimpleStringT::ReleaseBuffer.md)|緩衝區的釋放控制項所 `GetBuffer`傳回。|  
|[CSimpleStringT::ReleaseBufferSetLength](../Topic/CSimpleStringT::ReleaseBufferSetLength.md)|緩衝區的釋放控制項所 `GetBuffer`傳回。|  
|[CSimpleStringT::SetAt](../Topic/CSimpleStringT::SetAt.md)|設定字元在特定位置。|  
|[CSimpleStringT::SetManager](../Topic/CSimpleStringT::SetManager.md)|設定 `CSimpleStringT` 物件的記憶體管理員。|  
|[CSimpleStringT::SetString](../Topic/CSimpleStringT::SetString.md)|設定 `CSimpleStringT` 物件的字串。|  
|[CSimpleStringT::StringLength](../Topic/CSimpleStringT::StringLength.md)|傳回字元數所指定字串的。|  
|[CSimpleStringT::Truncate](../Topic/CSimpleStringT::Truncate.md)|截斷字串為指定之長度。|  
|[CSimpleStringT::UnlockBuffer](../Topic/CSimpleStringT::UnlockBuffer.md)|啟用計數的參考並釋放緩衝區中的字串。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CSimpleStringT::operator PCXSTR](../Topic/CSimpleStringT::operator%20PCXSTR.md)|直接存取在 `CSimpleStringT` 物件中的字元當成 C\+\+. 格式的樣式。|  
|[CSimpleStringT::operator](../Topic/CSimpleStringT::operator.md)|傳回字元包含在指定之位置的 `GetAt`—運算子取代。|  
|[CSimpleStringT::operator \+\=](../Topic/CSimpleStringT::operator%20+=.md)|新字串串連到現有字串的結尾。|  
|[CSimpleStringT::operator \=](../Topic/CSimpleStringT::operator%20=.md)|指派新值給 `CSimpleStringT` 物件。|  
  
## 備註  
 `CSimpleStringT` 是 Visual C\+\+ 所支援的各種字串類別的基底類別。  它在字串物件和基礎緩衝區作業的記憶體管理的最小支援。  如需更多進階的字串物件，請參閱 [CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
## 需求  
 **Header:** atlsimpstr.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)