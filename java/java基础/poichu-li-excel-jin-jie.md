public void setFileProperty\(File file,TemplateInfoParam param\) throws IOException{

 FileInputStream is=null;

 FileOutputStream out=null;

try{

 is= new FileInputStream\(file\);

 HSSFWorkbook workbook = new HSSFWorkbook\(is\);

 workbook.createInformationProperties\(\);//创建文档信息

 DocumentSummaryInformation dsi= workbook.getDocumentSummaryInformation\(\);//摘要信息

// dsi.setCategory\("类别:Excel文件"\);//类别

// dsi.setManager\("管理者:admin"\);//管理者

// dsi.setCompany\("公司:科融数据系统股份有限公司"\);//公司

 CustomProperties cusPro=dsi.getCustomProperties\(\);

 if\(null==cusPro\){

cusPro=new CustomProperties\(\);

 }

 cusPro.put\("templateCode",param.getTemplateCode\(\)\);

 cusPro.put\("templateVersion",param.getVersionId\(\)\);

 dsi.setCustomProperties\(cusPro\);

// SummaryInformation si = workbook.getSummaryInformation\(\);//摘要信息

// si.setSubject\("主题:银监报表"\);//主题

// si.setTitle\("标题:FA1601"\);//标题

// si.setAuthor\("作者:admin"\);//作者

// si.setComments\("备注:银监上报"\);//备注

 out=new FileOutputStream\(file\);

 workbook.write\(out\);

 }catch\(IOException e\){

 e.printStackTrace\(\);

 }finally{

if\(out!=null\){

out.close\(\);

}

if\(is!=null\){

is.close\(\);

}

 }

 }

