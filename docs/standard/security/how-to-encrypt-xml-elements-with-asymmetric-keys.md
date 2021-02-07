---
description: '자세한 정보: 방법: 비대칭 키를 사용 하 여 XML 요소 암호화'
title: '방법: 비대칭 키를 사용하여 XML 요소 암호화'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSA class
- asymmetric keys [.NET]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- encryption [.NET], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
ms.openlocfilehash: fff8ec57da0318e48f2a230f01dba26497837028
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685155"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="9ba7a-103">방법: 비대칭 키를 사용하여 XML 요소 암호화</span><span class="sxs-lookup"><span data-stu-id="9ba7a-103">How to: Encrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="9ba7a-104"><xref:System.Security.Cryptography.Xml> 네임스페이스의 클래스를 사용하여 XML 문서 내의 요소를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="9ba7a-105">XML 암호화는 데이터가 쉽게 읽혀질 염려 없이 암호화된 XML 데이터를 교환하거나 저장하는 표준 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-105">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="9ba7a-106">XML 암호화 표준에 대 한 자세한 내용은에 있는 XML 암호화에 대 한 World Wide Web 컨소시엄 (W3C) 사양을 참조 하십시오 <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="9ba7a-106">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="9ba7a-107">XML 암호화를 사용하여 암호화된 XML 데이터가 포함된 <`EncryptedData`> 요소의 문서나 XML 요소를 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-107">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="9ba7a-108"><`EncryptedData`> 요소는 암호화 중에 사용 된 키와 프로세스에 대 한 정보를 포함 하는 하위 요소를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-108">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="9ba7a-109">XML 암호화를 사용하면 문서에 암호화된 여러 요소가 포함될 수 있고 한 요소가 여러 번 암호화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-109">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="9ba7a-110">이 절차의 코드 예제에서는 `EncryptedData` 나중에 암호 해독 중에 사용할 수 있는 다른 여러 하위 요소와 함께 <> 요소를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-110">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="9ba7a-111">이 예제에서는 두 키를 사용하여 XML 요소를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-111">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="9ba7a-112">RSA 퍼블릭/프라이빗 키 쌍을 생성하고 보안 키 컨테이너에 키 쌍을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-112">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="9ba7a-113">그런 다음 AES(Advanced Encryption Standard) (AES) 알고리즘을 사용 하 여 별도의 세션 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-113">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm.</span></span>  <span data-ttu-id="9ba7a-114">이 예제에서는 AES 세션 키를 사용하여 XML 문서를 암호화한 다음 RSA 공개 키를 사용하여 AES 세션 키를 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-114">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="9ba7a-115">마지막으로,이 예제에서는 암호화 된 AES 세션 키와 암호화 된 XML 데이터를 새 <> 요소 내의 XML 문서에 저장 합니다 `EncryptedData` .</span><span class="sxs-lookup"><span data-stu-id="9ba7a-115">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="9ba7a-116">XML 요소를 암호 해독하려면 키 컨테이너에서 RSA 프라이빗 키를 검색하고 세션 키를 암호 해독하는 데 사용한 다음 세션 키를 사용하여 문서를 암호 해독합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-116">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="9ba7a-117">이 절차를 사용 하 여 암호화 된 XML 요소의 암호를 해독 하는 방법에 대 한 자세한 내용은 [방법: 비대칭 키를 사용 하 여 Xml 요소 암호 해독](how-to-decrypt-xml-elements-with-asymmetric-keys.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-117">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="9ba7a-118">이 예제는 여러 애플리케이션이 암호화된 데이터를 공유해야 하거나 애플리케이션이 실행되는 시간 사이에 암호화된 데이터를 저장해야 경우에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-118">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="9ba7a-119">비대칭 키를 사용하여 XML 요소를 암호화하려면</span><span class="sxs-lookup"><span data-stu-id="9ba7a-119">To encrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="9ba7a-120"><xref:System.Security.Cryptography.CspParameters> 개체를 만들고 키 컨테이너의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-120">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="9ba7a-121"><xref:System.Security.Cryptography.RSACryptoServiceProvider> 클래스를 사용하여 대칭 키를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-121">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="9ba7a-122"><xref:System.Security.Cryptography.RSACryptoServiceProvider> 클래스의 생성자에 <xref:System.Security.Cryptography.CspParameters> 개체를 전달하면 키가 자동으로 키 컨테이너에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-122">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="9ba7a-123">이 키는 AES 세션 키를 암호화하는 데 사용되며, 나중에 검색하여 암호 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-123">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="9ba7a-124">디스크에서 XML 파일을 로드하여 <xref:System.Xml.XmlDocument> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-124">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="9ba7a-125"><xref:System.Xml.XmlDocument> 개체는 암호화할 XML 요소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-125">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="9ba7a-126"><xref:System.Xml.XmlDocument> 개체에서 지정된 요소를 찾고 암호화할 요소를 나타내는 <xref:System.Xml.XmlElement> 개체를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-126">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="9ba7a-127">이 예제에서는 `"creditcard"` 요소가 암호화됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-127">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="9ba7a-128"><xref:System.Security.Cryptography.Aes> 클래스를 사용하여 새 세션 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-128">Create a new session key using the <xref:System.Security.Cryptography.Aes> class.</span></span>  <span data-ttu-id="9ba7a-129">이 키는 XML 요소를 암호화한 다음 자체 암호화되어 XML 문서에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-129">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="9ba7a-130"><xref:System.Security.Cryptography.Xml.EncryptedXml> 클래스의 새 인스턴스를 만들고 세션 키를 사용하여 지정된 요소를 암호화하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-130">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="9ba7a-131"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> 메서드는 암호화된 요소를 암호화된 바이트 배열로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-131">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="9ba7a-132"><xref:System.Security.Cryptography.Xml.EncryptedData> 개체를 생성하고 암호화된 XML 요소의 URL 식별자로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-132">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="9ba7a-133">이 URL 식별자를 통해 암호 해독하는 당사자가 XML에 암호화된 요소가 들어 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-133">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="9ba7a-134"><xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> 필드를 사용하여 URL 식별자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-134">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="9ba7a-135">Plaintext XML 요소는 `EncryptedData` 이 개체에 의해 캡슐화 된 <> 요소로 대체 됩니다 <xref:System.Security.Cryptography.Xml.EncryptedData> .</span><span class="sxs-lookup"><span data-stu-id="9ba7a-135">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="9ba7a-136">세션 키를 생성하는 데 사용되는 암호화 알고리즘의 URL 식별자로 초기화되는 <xref:System.Security.Cryptography.Xml.EncryptionMethod> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-136">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="9ba7a-137"><xref:System.Security.Cryptography.Xml.EncryptionMethod> 개체를 <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> 속성에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-137">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="9ba7a-138">암호화된 세션 키를 포함할 <xref:System.Security.Cryptography.Xml.EncryptedKey> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-138">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="9ba7a-139">세션 키를 암호화하고, <xref:System.Security.Cryptography.Xml.EncryptedKey> 개체에 추가하고, 세션 키 이름 및 키 식별자 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-139">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="9ba7a-140">암호화된 데이터를 특정 세션 키로 매핑하는 새로운 <xref:System.Security.Cryptography.Xml.DataReference> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-140">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="9ba7a-141">이 선택적 단계를 사용하면 XML 문서의 여러 부분이 단일 키로 암호화되었음을 쉽게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-141">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="9ba7a-142"><xref:System.Security.Cryptography.Xml.EncryptedData> 개체에 암호화된 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-142">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="9ba7a-143">새로운 <xref:System.Security.Cryptography.Xml.KeyInfo> 개체를 만들어 RSA 키의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-143">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="9ba7a-144"><xref:System.Security.Cryptography.Xml.EncryptedData> 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-144">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="9ba7a-145">이렇게 하면 암호 해독하는 당사자가 세션 키를 암호 해독할 때 사용할 올바른 비대칭 키를 식별하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-145">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="9ba7a-146"><xref:System.Security.Cryptography.Xml.EncryptedData> 개체에 암호화된 요소 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-146">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="9ba7a-147">원본 <xref:System.Xml.XmlDocument> 개체의 요소를 <xref:System.Security.Cryptography.Xml.EncryptedData> 요소로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-147">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="9ba7a-148"><xref:System.Xml.XmlDocument> 개체를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-148">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="9ba7a-149">예제</span><span class="sxs-lookup"><span data-stu-id="9ba7a-149">Example</span></span>  

 <span data-ttu-id="9ba7a-150">이 예제에서는 `"test.xml"`이라는 파일이 컴파일된 프로그램과 동일한 디렉터리에 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-150">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="9ba7a-151">또한 `"test.xml"`에 `"creditcard"` 요소가 포함되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-151">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="9ba7a-152">`test.xml`이라는 파일에 다음 XML을 배치하고 이 예제에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-152">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ba7a-153">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="9ba7a-153">Compiling the Code</span></span>  
  
- <span data-ttu-id="9ba7a-154">.NET Framework를 대상으로 하는 프로젝트에서에 대 한 참조를 포함 `System.Security.dll` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-154">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="9ba7a-155">.NET Core 또는 .NET 5를 대상으로 하는 프로젝트에서 NuGet 패키지 [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-155">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="9ba7a-156"><xref:System.Xml>, <xref:System.Security.Cryptography> 및 <xref:System.Security.Cryptography.Xml> 네임스페이스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-156">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="9ba7a-157">.NET 보안</span><span class="sxs-lookup"><span data-stu-id="9ba7a-157">.NET Security</span></span>

<span data-ttu-id="9ba7a-158">대칭 암호화 키를 일반 텍스트로 저장하거나 컴퓨터 간에 일반 텍스트로 대칭 키를 전송하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-158">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="9ba7a-159">또한 비대칭 키 쌍의 프라이빗 키를 일반 텍스트로 저장하거나 전송하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-159">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="9ba7a-160">대칭 및 비대칭 암호화 키에 대 한 자세한 내용은 [암호화 및 암호 해독을 위한 키 생성](generating-keys-for-encryption-and-decryption.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-160">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="9ba7a-161">소스 코드에 직접 키를 포함하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-161">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="9ba7a-162">포함 된 키는 [Ildasm.exe (IL 디스어셈블러)](../../framework/tools/ildasm-exe-il-disassembler.md) 를 사용 하거나 메모장과 같은 텍스트 편집기에서 어셈블리를 열어 어셈블리에서 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-162">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
<span data-ttu-id="9ba7a-163">암호화 키를 사용하여 작업이 완료되면 각 바이트를 0으로 설정하거나 관리되는 암호화 클래스의 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 메서드를 호출하여 메모리에서 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-163">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="9ba7a-164">디버거가 메모리에서 암호화 키를 읽거나 메모리 위치가 디스크에 페이징된 경우 하드 드라이브에서 읽을 수 있는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba7a-164">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba7a-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ba7a-165">See also</span></span>

- [<span data-ttu-id="9ba7a-166">암호화 모델</span><span class="sxs-lookup"><span data-stu-id="9ba7a-166">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="9ba7a-167">암호화 서비스</span><span class="sxs-lookup"><span data-stu-id="9ba7a-167">Cryptographic Services</span></span>](cryptographic-services.md)
- <span data-ttu-id="9ba7a-168">[플랫폼 간 암호화](cross-platform-cryptography.md)- <xref:System.Security.Cryptography.Xml></span><span class="sxs-lookup"><span data-stu-id="9ba7a-168">[Cross-Platform Cryptography](cross-platform-cryptography.md)- <xref:System.Security.Cryptography.Xml></span></span>
- [<span data-ttu-id="9ba7a-169">방법: 비대칭 키를 사용하여 XML 요소 해독</span><span class="sxs-lookup"><span data-stu-id="9ba7a-169">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](how-to-decrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="9ba7a-170">ASP.NET Core 데이터 보호</span><span class="sxs-lookup"><span data-stu-id="9ba7a-170">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
