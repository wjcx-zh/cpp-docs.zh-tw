---
title: "CPathT Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CPathT"
  - "CPathT"
  - "ATL::CPathT<StringType>"
  - "ATL::CPathT"
  - "ATL.CPathT<StringType>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPathT class"
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
caps.latest.revision: 20
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPathT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示路徑。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template< typename   
      StringType  
      >   
class CPathT  
```  
  
#### 參數  
 `StringType`  
 使用的來源字串類別的路徑 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)\(請參閱\)。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CPathT::PCXSTR](../Topic/CPathT::PCXSTR.md)|這是常數字串型別。|  
|[CPathT::PXSTR](../Topic/CPathT::PXSTR.md)|資料型別。|  
|[CPathT::XCHAR](../Topic/CPathT::XCHAR.md)|字元型別。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPathT::CPathT](../Topic/CPathT::CPathT.md)|路徑的建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPathT::AddBackslash](../Topic/CPathT::AddBackslash.md)|呼叫這個方法會將反斜線至字串的結尾建立路徑的正確語法。|  
|[CPathT::AddExtension](../Topic/CPathT::AddExtension.md)|呼叫這個方法會將副檔名加入至路徑。|  
|[CPathT::Append](../Topic/CPathT::Append.md)|呼叫這個方法會將字串附加至目前的路徑。|  
|[CPathT::BuildRoot](../Topic/CPathT::BuildRoot.md)|呼叫這個方法會從指定的加速數字的根路徑。|  
|[CPathT::Canonicalize](../Topic/CPathT::Canonicalize.md)|呼叫這個方法將路徑轉換成標準格式。|  
|[CPathT::Combine](../Topic/CPathT::Combine.md)|呼叫這個方法來串連字串表示目錄名稱和表示檔案路徑名稱的字串輸入路徑。|  
|[CPathT::CommonPrefix](../Topic/CPathT::CommonPrefix.md)|呼叫這個方法會判斷指定的路徑是否與目前的路徑共用相同前置詞。|  
|[CPathT::CompactPath](../Topic/CPathT::CompactPath.md)|呼叫這個方法會將檔案路徑在特定像素寬度適合透過取代路徑元件和橢圓形。|  
|[CPathT::CompactPathEx](../Topic/CPathT::CompactPathEx.md)|呼叫這個方法會將檔案路徑在字元內的許多適合透過取代路徑元件和橢圓形。|  
|[CPathT::FileExists](../Topic/CPathT::FileExists.md)|呼叫這個方法會檢查此路徑名稱的檔案是否存在。|  
|[CPathT::FindExtension](../Topic/CPathT::FindExtension.md)|呼叫這個方法會尋找副檔名的位置路徑中的。|  
|[CPathT::FindFileName](../Topic/CPathT::FindFileName.md)|呼叫這個方法會尋找檔名的位置路徑中的。|  
|[CPathT::GetDriveNumber](../Topic/CPathT::GetDriveNumber.md)|呼叫這個方法會搜尋路徑" A "到" Z "的範圍內的磁碟機代號和傳回對應之提升數字。|  
|[CPathT::GetExtension](../Topic/CPathT::GetExtension.md)|呼叫這個方法會從路徑取得副檔名。|  
|[CPathT::IsDirectory](../Topic/CPathT::IsDirectory.md)|呼叫這個方法會檢查路徑是否為有效的目錄。|  
|[CPathT::IsFileSpec](../Topic/CPathT::IsFileSpec.md)|呼叫這個方法會搜尋路徑的所有路徑中分隔的字元 \(例如， 「: 」或「\\」\)。  如果沒有目前路徑中分隔的字元，路徑視為檔案 Spec 路徑。|  
|[CPathT::IsPrefix](../Topic/CPathT::IsPrefix.md)|呼叫這個方法會判斷路徑是否含有 `pszPrefix`傳入的型別有效的前置字元。|  
|[CPathT::IsRelative](../Topic/CPathT::IsRelative.md)|呼叫這個方法會判斷路徑是否相對於的。|  
|[CPathT::IsRoot](../Topic/CPathT::IsRoot.md)|呼叫這個方法會判斷路徑是否為目錄的根。|  
|[CPathT::IsSameRoot](../Topic/CPathT::IsSameRoot.md)|呼叫這個方法會判斷其他路徑是否具有目前路徑的通用根元件。|  
|[CPathT::IsUNC](../Topic/CPathT::IsUNC.md)|呼叫這個方法會判斷路徑是否為伺服器和共用有效的 UNC \(通用命名慣例 \(Universal Naming Convention，UNC\) 路徑。|  
|[CPathT::IsUNCServer](../Topic/CPathT::IsUNCServer.md)|呼叫這個方法會判斷路徑是否只會在伺服器上的有效的 UNC \(通用命名慣例 \(Universal Naming Convention，UNC\) 路徑。|  
|[CPathT::IsUNCServerShare](../Topic/CPathT::IsUNCServerShare.md)|呼叫這個方法會判斷路徑是否為有效的 UNC \(通用命名慣例 \(Universal Naming Convention，UNC\) 共用的路徑，例如\\ \\ server \\ share。|  
|[CPathT::MakePretty](../Topic/CPathT::MakePretty.md)|呼叫這個方法將路徑轉換成小寫字母將路徑提供一致的外觀。|  
|[CPathT::MatchSpec](../Topic/CPathT::MatchSpec.md)|呼叫這個方法會搜尋路徑包含萬用字元比對類型的字串。|  
|[CPathT::QuoteSpaces](../Topic/CPathT::QuoteSpaces.md)|其中包含任何空白，請呼叫這個方法使用引號括住路徑括住。|  
|[CPathT::RelativePathTo](../Topic/CPathT::RelativePathTo.md)|呼叫這個方法會從一個檔案或資料夾的相對路徑至另一個。|  
|[CPathT::RemoveArgs](../Topic/CPathT::RemoveArgs.md)|呼叫這個方法會從路徑移除任何命令列引數。|  
|[CPathT::RemoveBackslash](../Topic/CPathT::RemoveBackslash.md)|呼叫這個方法會從路徑移除此行尾端反斜線。|  
|[CPathT::RemoveBlanks](../Topic/CPathT::RemoveBlanks.md)|呼叫這個方法會從路徑中移除所有的前置和尾端空格。|  
|[CPathT::RemoveExtension](../Topic/CPathT::RemoveExtension.md)|如果有的話，呼叫這個方法會從路徑移除副檔名。|  
|[CPathT::RemoveFileSpec](../Topic/CPathT::RemoveFileSpec.md)|如果有，呼叫這個方法會從路徑移除此行尾端的檔案名稱和反斜線。|  
|[CPathT::RenameExtension](../Topic/CPathT::RenameExtension.md)|在路徑中呼叫這個方法取代延伸用新的擴充功能。  如果檔案名稱不包含副檔名，副檔名會附加至字串的結尾。|  
|[CPathT::SkipRoot](../Topic/CPathT::SkipRoot.md)|呼叫這個方法會解析路徑，忽略磁碟機代號或 UNC 共用伺服器\/路徑部分。|  
|[CPathT::StripPath](../Topic/CPathT::StripPath.md)|呼叫這個方法會移除完整路徑和檔名的路徑部分。|  
|[CPathT::StripToRoot](../Topic/CPathT::StripToRoot.md)|呼叫這個方法會移除路徑的所有組件除了根目錄資訊。|  
|[CPathT::UnquoteSpaces](../Topic/CPathT::UnquoteSpaces.md)|呼叫這個方法會從的開頭移除路徑的引號和結尾。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CPathT::operator const StringType &](../Topic/CPathT::operator%20const%20StringType%20&.md)|這個運算子可讓物件會被視為字串。|  
|[CPathT::operator CPathT::PCXSTR](../Topic/CPathT::operator%20CPathT::PCXSTR.md)|這個運算子可讓物件會被視為字串。|  
|[CPathT::operator StringType &](../Topic/CPathT::operator%20StringType%20&.md)|這個運算子可讓物件會被視為字串。|  
|[CPathT::operator \+\=](../Topic/CPathT::operator%20+=.md)|這個運算子會將字串附加至路徑。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPathT::m\_strPath](../Topic/CPathT::m_strPath.md)|路徑。|  
  
## 備註  
 `CPath`、 `CPathA`和 `CPathW` 是 `CPathT` 具現化的定義如下:  
  
 `typedef CPathT< CString > CPath;`  
  
 `typedef CPathT< CStringA > CPathA;`  
  
 `typedef CPathT< CStringW > CPathW;`  
  
## 需求  
 **Header:** 類別  
  
## 請參閱  
 [類別](../../atl/reference/atl-classes.md)   
 [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md)