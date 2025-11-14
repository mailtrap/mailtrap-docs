---
description: >-
  Create and send Mailtrap email templates: design with drag-and-drop builder or
  HTML editor, add Handlebars variables, and integrate via API or SMTP.
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Email Templates

### Overview  <a href="#overview-qnotn" id="overview-qnotn"></a>

Email Templates allow you to design, edit, and host HTML email templates, and reference them via API.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdVMgbBV8K63DIAobALhk_Kp-l8dv6KkOh52QxRHvai0pvNN5SPcDOhfegDA1oNB11y1kgj4joLrc8m8-ds_KTvakzrlzG3VR0HZi3ehQGtjnKsExhiv4NAQZRt1KLUJhDxOzlW_SgcqCXa7GDAWoEfVmM?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>

By storing the template on Mailtrap and calling it via API, you can easily change the template code without committing to your codebase.

Email Templates support Variables, and Mailtrap uses Handlebars as a template engine.

You can put \{{user\_name\}} into your template and pass “John” as the “user\_name” value via API.

{% embed url="https://mailtrap.io/blog/using-handlebars-with-mailtrap-email-templates-quick-guide-with-examples/" fullWidth="false" %}

### Creating a template  <a href="#creating-a-template-hseff" id="creating-a-template-hseff"></a>

{% stepper %}
{% step %}
Navigate to the Templates menu

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeM4SWbLeil8YG5eiPe_HizwvxYzU2POSwTK6MoXgcelIvl7FTg7jvZ2WOku_7C8CThZZ0-1jDJ7vthPQXyjMCtdznsenu6X40gjeGSiN2BxFDxa4Dp1-ls4q-5FqUcIJoaIzrMp0F4OvdpNd5mkvNy0MBQ?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="375"></div>
{% endstep %}

{% step %}
Click the Create New Template button.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXda86cFCtOQaZBXoOeP9jdtwg5D29yco-MHeQKz__eMdDFWStQKTUzDi29r-62FtXEcApZ5PEdLXzvrR8aj6HEWvfNyzIkvD7u_9wegkYysapyTWu2UVdQD6-VDDol_mw2KvHjC-uglHHR3oSEmHyl98YxC?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>
{% endstep %}

{% step %}
Click the drop-down menu to select one of your domains, enter the Template name, Subject, and Category, and click Continue.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeSWAisognZo94YPxPlT4493JqfVfxDT-B2AjzEZ6eJCFbpT2xZocN8FAKiFHNNuXEsmdbvGvcvv3XXU9WGBG11K_R3bMa1hp8uYYZvdYq5b_2MRzgaleGdN6MpJIN8NA3GUEHNfGKJxcvdcHsNk5g8Yb_o?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="375"></div>
{% endstep %}

{% step %}
Choose the Drag & Drop Editor to build the template without coding, or select HTML Editor if you prefer to write/modify the code.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfYY4inSpayS1S-byv3tYFN4PdtAkgUXJajT9SXm2e6gDVNz2gFQ9q3ZdEXPA8g7EA_hK2oysgU9XEEBF2jhKBZWB6UvmTBjPTccb-9-kapPioXV_KehiV9TXwzneFuS6d4b58NaXb-TE0ClQ5JevrXpmbq?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="375"></div>
{% endstep %}

{% step %}
Create/modify the design and click Finish.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeqEVCiMdSqSRC-zXFXPwLy8Bq5YKiEONhJHhcqXgWJF8-XOGdCVhcsTDwkv6u7s3JHtkzKbNWgGmm_dRD-7b0QAZyvrdvFfNQojzzMBeyjxQjSkg2CfprI95b1fL1TICU1-KDqKvEWq8YUNtxN_46a3Xc?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>

The main Templates menu features all your saved templates. To quickly access a saved template, just click on it within the main menu.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdHgWfiQiidpixCpcqTezevMUWbLdMgwP2N0O4aK3rQv_TTi3efrfu_ydWt9UVaAQeb33765HqGoqd_OBsm9KL69CmcQGCDlRSQgx5nTFigFWp0INujpSC3Nb_KfC828VocMKAe8TYcnIOB0enMvR83xayJ?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>
{% endstep %}
{% endstepper %}

### Editing and customizing templates  <a href="#editing-and-customizing-templates-uztqb" id="editing-and-customizing-templates-uztqb"></a>

#### Details

Each template must have a name, subject, category, and assigned domain. The subject also supports variables.

![](https://lh7-us.googleusercontent.com/docsz/AD_4nXdnRJfeMLg0o3Mee62WMx3xLuVrKF-vwLAj2iQj_CV-N5MRZLQYFiJ7WYYPPT_6FVBrdX48Vm8he_vgwdMc0oZmTnz7JnfUHtYTQiLSXU9jZMNxbH30dsZYObYDSZBTRQMKjVoR6vxtkFl_no7Y78ZVV7uF?key=NN3Gxq3jJKukm_ofXN_gsg)

#### Drag & Drop Editor <a href="#drag-drop-editor-7ciir" id="drag-drop-editor-7ciir"></a>

The drag-and-drop editor allows you to design templates without any coding.

![](https://lh7-us.googleusercontent.com/docsz/AD_4nXcCkfg6cL5eVTbSuIyJ7PkNk1iZwlUDqwhBIPLIUlonJRAUBsKYphPxONNLmTcGP-Z1R-ZygerbTe4HY2LhikATGyIQfOTeFQ8AsgyGTnuGxI7KpW0r-5-otQTJJhQMQ4aE5pOkMB-S7AZxLC5T0Y-L_Hif?key=NN3Gxq3jJKukm_ofXN_gsg)

#### Code Editor <a href="#code-editor-ygtr7" id="code-editor-ygtr7"></a>

Code Editor allows you to edit the HTML or Text content, depending on the emails you want to send.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeaNPgqgB7PnX4p1gQodK7tRFAuPt64bdsdO_eJBOEiMl-Ieh90vz1vD81SuRY_vEGqfa7JW3JY2CK_l_y92FeZBNh2u-5s5SZDahGZsspJtIwu9sHVk5-k4kF2FaDynl9mhI2H3p2mGu_5tS2BNmVIGjde?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>

The editor supports Find and Replace options, and you can use Cmd+F or Win+F as a hotkey to reveal a quick search bar.

If your template has an error, Handlebars cannot render it. You’ll see an error message in the Preview tab, and the RAW code with an error will be highlighted in the Editor.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdcTsvxwefaCp-tDkxoP8eMp6h7GeIXTHw92wYbCzPnWVxHa8ZgZzDOOgxEpKkrvhLBOZYStUQ2rILlQPBVUJpPPFH8NdkRfgboNv9byAJUj8VkoDP7vrH2iAIcc1drxA7JcJ72aFGqB8IJi7NBSF2CDhyT?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>

You can’t save a template with errors, either. Remember that we don’t validate HTML.

**Uploading an image**

{% stepper %}
{% step %}
Click Upload image in the upper right corner of the Code Editor.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXd3AxO5uv_cz0fxP2rjn2bzfn9X1rRx-n_70ItP3a5AemZv-xerE5SZV-pXGyTlHLRn63f4tCNZbsvGgFEV_s-F7en8azGIArG5oaZyE-J-HZhWQoOahGVeTB-hb6GrQrxBxD3xiOOxDQRNOQdOn_LEdwtB?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="375"></div>
{% endstep %}

{% step %}
Hit the Upload New button in the following menu and choose an image from your local drive (Supported formats are JPG, PNG, and GIF, and the maximum file size is 2 MB).

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfcWHQMTnMKQv-fQuD9bKJd9Ve_eDmBk_R-cS7B7uZYiYYxOcsQl8EwNdhWoYlZFnCZyJ21b6rgHxSNeEZGH2qsCwv9NESIadNUXbErNPt6K1BZ8fDIbUCkritLade9zvRV4WVsh2LLYT7j-C6bmxU1fBbM?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>
{% endstep %}

{% step %}
Once the image is uploaded, you will receive a confirmation notification. If the file format is unsupported or the image is too big, you will receive the corresponding error message.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/668564271f3fa9421e288bc7/file-4aamBukxrj.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Click the Copy URL button to copy the image URL to your clipboard, then click Template to return to the editing menu.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXf6IebcjVoxWdfX6HjSTpS-L0W45Iz-31nsezygOr4NGCP3SDMvEViyBC2PGCTznAjEdEBTC_ICPF8iwQBuWJNS--cqnue0yZsYFzhw7S4abpnZ1tBzQ1nJ9Yxr92qzkxWtDIH6vwc3J0m7F5a6yyMfBTtg?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>
{% endstep %}

{% step %}
Proceed to add the image to the template body under the `<img>` tag. You can preview it in the template as soon as the asset is added.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfS-zfnCteRJ7Pa1IKZ04EV_H9NaN0sweiGwixOxumHscgJrxFviu7puRUDb9b30UCR6vs6Yh0OxN7rVfe_sLr-YYkjMlFpH4ogUj7_XR2vyHfuBDxeXJurTYHfh6ZprSSYgCgK-RfdVfJksxa_AA_Lbdo?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="375"></div>
{% endstep %}
{% endstepper %}

**Test Data**

Code Editor automatically parses your template and shows all the variables found. The Test Data tab helps you preview the object variables.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdUCEiKTl7r9Lex1qKSF3vjuiGCYGJHZZLvL__0SO3J8H8_fFx_PqGBhLPRADGGxVPRhls2YM0DflC5Ro9Bxt5gLpgurkN6AkkEYQJwM4sWrnkWd2isaJqutbdMDSNua8WTLw0gOeMoq1Opg0qbDhhXoWE?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>

By default, as a value, we put a variable name and add the “Test\_” prefix.

#### Send test

If you’re using email templates in production, you can send a test email to the account owner's email address to run basic tests. Simply press the Send Test button.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdkPQ2zPnezvh0zl-3VgCX0U1hAt6WM6EAxPjNmhidoaP45DGOccIHaCp6ZEUYnTj0KE6RFXGD4kkrj9t1M24et7T2RVEuUaFywAgq4xz0kamzX0xvY2sIIJKIN-Gnw1bfI4HerVl7RHdSs3DHjJZL54qq4?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>

Important Notes:

* Your domain should be verified to send a test.
* Each test email is billed over your quota.

### Template integration - Email API/SMTP  <a href="#template-integration-email-apismtp-wipdp" id="template-integration-email-apismtp-wipdp"></a>

{% stepper %}
{% step %}
Navigate to Templates in the menu on the left.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcNbJzknDPq35eUmqlM1hehmhSbGOFYIrIwm1fgawByHaZQyyVVAJM-GiClji_pQKsI1hWk2lWndM_hcffFlef50pmGeDLTObE8F6sudC5a0kvU4ifCzyBwAY5YY6fimet1tHIoO0U4VOKzzDA9N5YfAned?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="375"></div>
{% endstep %}

{% step %}
Click the template you want to call using the API.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXddqb4Nrf5iMFeULLUJFez1N8QVTACZanicvZCp9aEl6Rw3LgfxxlUYT6-Noiy36R2Tt-Ji-Lw8qlIOOVo12g_Cem-pjze8Xu0HM5XMPoWrczjHS6xn99d7SyoawKwou5BHXEBL5naGC27otlvGsyBZ2L0?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>
{% endstep %}

{% step %}
Open the Integration tab.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcNiBeCjcL8Fjd3LydLsQs7Yni5SxOmWoyKS97e_R7G5KNNIqBgS8YAeXAPULgbIEs7tPdjb75Fpu_sF-vk89PAtntciQ-KL27T0qdgDGj7NTyRkSQPy2qE-e6HZKmkoL-s5GUEiYxP5say4fMrGQkAsUc7?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>
{% endstep %}

{% step %}
With Email API/SMTP toggled on, click Integrate under Transactional Stream or Bulk Stream.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeaoT5GDxde5kLR2d6_NYj1aEvrM7DxD7cpGjB_oN6a7sZ8kkkCH6M-N_GxOVGkDqfCdl5gdRtoTu2Uxlg0Zx20YZlbumYXrb7McU7EiD-o5d31RhC6jAQLTogrEd_xJKsHr8yGrUURuac3cc4uOVd2uD93?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>
{% endstep %}

{% step %}
Copy the necessary credentials such as Host, API Token, and Template UUID.

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdols8rnCS-t-G3IqJhCpYq5BFlTCZBk9SOnsHC9tyo1WWs88m7rv2NqTBybZi9fyyvIsJV4E6q1oqyaD51RHU9J5X-NQE8iCRIjpnM6Qd0Ep7tw6J5c6wvwbyi9LUbg84sQItFByg2XkF_V-MCu9S5W2E?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"><figcaption><p>Transactional Stream API credentials</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfgBFVpK6H_G2K-onlqL8M_uraddoRp-w946zRCAidenn_r0q0r03OcfrSJGms1NyW7yYaedmCQ0AWT_C6Oi4_o__oPJKYlTr6AmbnpNd3NkGC7jUYFI1Zt9tmESSCUO33CQITZw4bMLBXEVSF1tE2-OHI?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"><figcaption><p>Bulk Stream API credentials</p></figcaption></figure></div>
{% endstep %}

{% step %}
Alternatively, under Code Samples, choose the desired language and copy the sample configuration already containing the necessary credentials. Mailtrap’s official SDKs ([Node.js](https://github.com/railsware/mailtrap-nodejs), [Python](https://github.com/railsware/mailtrap-python), [PHP](https://github.com/railsware/mailtrap-php), and [Ruby](https://github.com/railsware/mailtrap-ruby)) also support the templates feature.
{% endstep %}

{% step %}
Paste the code into your project and customize it if needed. Then, run the code to send an email to the email address you indicated in your script.

For more details, [open the API docs](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api) and go to Email Sending API → Emails → Send email (including template) for transactional stream and Bulk Sending API → Emails → Send email (including template) for bulk stream. Under Body, click the dropdown menu, and choose `EmailFromTemplate` .
{% endstep %}
{% endstepper %}

### Template debugging  <a href="#template-integration-email-testing-p43ih" id="template-integration-email-testing-p43ih"></a>

{% stepper %}
{% step %}
Navigate to Templates in the menu on the left.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcfOoSBpzQJ6QubB6Cz4ZG0s6bvZ7PAlygoBlwpTwQBYSW8dEpgWgmprmIJM9uu2_QYtjUrwztt4bxr7GEQhlXKZLqRvSAmusgNNqrH-ttJ2pBG3jqsIQ7DXsDNU7CxpkVHu5AuAHCFApt1F8-3aBDSqtH9?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="375"></div>
{% endstep %}

{% step %}
Click the template you want to call using the API.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcY59GFRwUSnie9b6i_8dqSu-N252zl543hx2wEtZQR-YAz_m-qzTUj4u96M6c8oRFjvDkc5LH7LdhIj5jfhKr3osh-a0uKagEYgjFlVB5WWenqipDAv2U4lI2zsMjodDe0s90wVmnXbFMKlTamTs3HU1s?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>
{% endstep %}

{% step %}
Open the Integration tab.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfsHu1bHmwY7RXTHlVPrfNoxVWmr35OgYRmqQP_Ywu_H_7lCXHmbgKsy0bH0jnavzjleIBZq_LPI3D9HZ6Y7H7mdQSmdw50zWcuMOTXEJdR_EM2OgQkQGiW5vEwDb7_zFqNuT_K4s13ADtZiAHHu8F3qN9e?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>
{% endstep %}

{% step %}
Toggle the switch to Email Testing.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfey0RQK85C1ODl76hYdJqB8bUBXuT_ktLg28bom-ZNEsqxKEt6YqfX5oNH3wP9FRXj0QPZ7GYL8RQfxq7z37JYJczgDMRkSq0GF6f4E4cV4050VlD5S_Mfh8NCmiBVTn7fMKJ0N_X8TL4oiiwW_6ROI1A?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="375"></div>
{% endstep %}

{% step %}
And click Integrate.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcV6fyry4zcSpZpitMqCIrqBgEBXR3JSwoCFQ7LTgsOc-6SEPjWS0kMkd_QfLHQMGec51lMn9aODbD8gMwL8Lk3s_lepZMEJEGwQQ4mVTdAOtu778H79pbS7P_hULrV4X93L0LVmZWwWHyo_f7q5s2tpYPV?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="375"></div>
{% endstep %}

{% step %}
Select the desired sandbox from the dropdown menu to reveal its credentials. Copy the Host, API Token, Template UUID, and Sandbox ID.

Alternatively, you can also use one of the pre-made Code Samples.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfvgcMHF3nlAdE3iDNd98QgXbfv4pxn2DngHAj8tTNOn-8G8w2BUt8YfMsM6IVRqv9FOqUnY_uXEnNEC3YFoyC0SUrWDhxuKT7mw_p8P2vlbKEqPt4JT5Ei7wfOrgSCIQCEQE0JXKlHS6Vb3DS6pS3z3Z_8?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>
{% endstep %}

{% step %}
Paste the code into your project and customize it if needed. Then, run the code to send an email to the selected Email Testing sandbox.
{% endstep %}

{% step %}
Finally, check the sandbox you specified in the script.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeLw2SwKhAjjyeqVh2MSo-dPNogmm4Mv8uvMr6t16FL15IlIO4e36g0ZVaOhEDTkz4LpXbQCfa2q146InoArAQt96rmXC7lC2B52-UvhsIiO73s6Ek1FvsCSZjue4-Sez9RGN7PVc86yFGqnRJho3tUM1fD?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>

The Tech Info tab contains the link to the template you tested and lists all the variables used in the template.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6685668edd0f8c60bb3fde3a/file-3E9GDx2mDL.png" alt="" width="563"></div>

For more details, [open the API docs](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api) and go to [Sandbox API](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-email-testing-api) → Test Emails → Send email (including templates). Under Body, click the dropdown menu, and choose `EmailFromTemplate` .
{% endstep %}
{% endstepper %}

### List of templates and user permissions <a href="#list-of-templates-and-user-permissions-5xa8x" id="list-of-templates-and-user-permissions-5xa8x"></a>

Clicking on Templates in the side menu lists all the templates you can access.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfiDfPL2uGcpJuArmgMEtsMXbzkKJjjtSz0BLJ0q8tUuXKSXhft6RlPMEyXcDGS_u_X9901zBwcPfZOpog9Mq4KbKZ4ty1ammFQUzOZFtE71D4XtR8Xr_TWro_F3cTLZjptpdcddfp-KQrWyyqlNCnlEFje?key=NN3Gxq3jJKukm_ofXN_gsg" alt="" width="563"></div>

Access to templates is managed on a domain level. You need to have Admin access to a domain to manipulate the templates. In case you don’t have Edit rights, you can’t change the template. Each account can have up to 200 email templates.

{% hint style="warning" %}
_You can delete a template. However, this action is irreversible, so be sure to change the sending/testing code after deletion. When the template is deleted, the UUID is also deleted, and Mailtrap won’t be able to render it._
{% endhint %}

