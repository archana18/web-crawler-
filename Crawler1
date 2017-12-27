package crawler1;

import java.io.IOException;
import java.util.HashMap;

import org.jsoup.Connection;
import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

public class NJsoupRun {
	static String[] a = new String[10000];
	static String[] b = new String[10000];
	static String url1;
	static String[] title= new String[10000];
	static String[] titledate = new String[10000];
	static int j=0;
	static String[] date = new String[10000];
	static int l1;
	static HashMap<String,String> hash;
	
	public static int check(String url) throws IOException
	{
		if(url.contains("binghamton.edu/research") && !(url.endsWith("#")))
		{
			//print("test");
			if((url=="http://www.binghamton.edu/research")|| ((url.endsWith(".html"))||(url.endsWith("/"))))
					{//print("test");
		if(url.contains("mailto"))
			return 0;
		if(url.contains("pdf"))
			return 0;
		if(url.contains("documents"))
				return 0;
		else if(url.contains("http://discovere.binghamton.edu/"))
			return 0;
		
		else if(url.isEmpty())
			return 0;
		else
			return 1;
		}}
		
			return 0;
		
	}
	private static int status(String url) {
		// TODO Auto-generated method stub
		try {
			if(check(url) == 1){
				Connection.Response response = Jsoup.connect(url).userAgent("Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/535.21 (KHTML, like Gecko) Chrome/19.0.1042.0 Safari/535.21").timeout(10000).execute();
				int statusCode = response.statusCode();
				if((statusCode==404))
				{//print("test");
				return 0;
			
				}
					
					else if(!((199 < statusCode )&&(statusCode< 299)))
						return 0;
					else
						return 1; 
		} 
		}catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		return 0;
	}

	
	public static void Crawl1(String url,HashMap<String,String> hash) throws IOException {
		int i=0;
		
		int lim = 0;
		
		
			if(check(url)==1)
		
		{
			
			Document doc = Jsoup.connect(url).get();
			Elements links = doc.select("a[href]");
			l1=links.size();
			for (i = 0; i < links.size(); i++) {
				try{	
				Element link = links.get(i);
				
				a[i] = link.attr("abs:href");
				if(check(a[i])==1 && status(a[i]) == 1)
				{
					b[j]=a[i];
					Document doc3 = Jsoup.connect(b[j]).get(); 
					 Elements title1 = doc3.select("meta[property=og:title]");
					   
						//if (title1!=null) {
					    	//title[j]= title1.attr("content");
					   // }
					    //else {
					    	title[j] = doc3.title();
					    //}
				
					Elements link1 = doc3.getElementsByClass("dired");
					date[j] = link1.text();
					titledate[j]= title[j]+" \t"+date[j];
					hash.put(b[j], titledate[j]);
				
				
				
				
				
				
				j++;
				lim++;
			} }
				catch (IOException e) {
					System.out.println("Error page not found");
					continue;
				}
		}
			
		
			

		}
		
	}
			
		
	
			
		



public static void main(String[] args) throws IOException {
	int lim = 0;
	hash = new HashMap<String,String>();
	String url = "http://www.binghamton.edu/research";
	 Crawl1(url,hash);
	
	int i = 0;
	
	for (i = 0; i < l1; i++) {
		{
			
			if (check(b[i])==1)
					
				url1 = b[i];
				url1.trim();
				Crawl1(url1,hash);
			
			}

		}

	System.out.println(hash.toString().replaceAll(",", "\n").replaceAll("Last Updated:", "  \t").replaceAll("=", "  \t"));
	}

	

private static void print(String msg, Object... args) {
	System.out.println(String.format(msg, args));
}

private static String trim(String s, int width) {
	if (s.length() > width)
		return s.substring(0, width - 1) + ".";
	else
		return s;
}
}
