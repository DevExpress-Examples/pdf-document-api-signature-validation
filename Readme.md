<!-- default badges list -->
![](https://img.shields.io/endpoint?url=https://codecentral.devexpress.com/api/v1/VersionRange/775406630/23.2.3%2B)
[![](https://img.shields.io/badge/Open_in_DevExpress_Support_Center-FF7200?style=flat-square&logo=DevExpress&logoColor=white)](https://supportcenter.devexpress.com/ticket/details/T1223968)
[![](https://img.shields.io/badge/📖_How_to_use_DevExpress_Examples-e9f6fc?style=flat-square)](https://docs.devexpress.com/GeneralInformation/403183)
<!-- default badges end -->
# PDF Document API – Validate Document Signatures

The following sample project uses the DevExpress PDF Document API to generate signature validation reports.

To test, simply click **Browse** to load the desired PDF file. If the file contains signatures, the table will display signature information as pictured below.

![image](./media/pdf-signature-validator-main.png)

## Implementation Details

The [GetSignatureInfo](https://docs.devexpress.com/OfficeFileAPI/DevExpress.Pdf.PdfDocumentSigner.GetSignatureInfo) method retrieves all signatures contained in the PDF file. Each signature from this list is then passed as the `GenerateInfoList` method parameter. This method retrieves signature name, signer’s name, and certificate information to generate the information list. The [VerifySignature](https://docs.devexpress.com/OfficeFileAPI/DevExpress.Pdf.PdfPkcs7Signature.VerifySignature) method verifies signature validity. The generated list is then displayed in a [DxDataGrid](https://docs.devexpress.com/Blazor/DevExpress.Blazor.DxDataGrid-1?) table.

## Files to Review

* [Index.razor](./CS/Pages/Index.razor)

## Documentation

* [How to: Validate a PDF Document Signature](https://docs.devexpress.com/OfficeFileAPI/404728/pdf-document-api/examples/document-protection/how-to-validate-a-pdf-document-signature)

## More Examples

* [PDF Document API - Sign a PDF Document with a Certificate Stored on a Hardware Device](https://github.com/DevExpress-Examples/pdf-document-api-sign-documents-with-certificate)
* [PDF Document API - Use the Azure Key Vault API to Sign a PDF Document](https://github.com/DevExpress-Examples/pdf-document-api-use-azure-key-vault-api-to-sign-document)
* [PDF Document API - Apply Multiple Signatures](https://github.com/DevExpress-Examples/pdf-document-api-multiple-signatures)
