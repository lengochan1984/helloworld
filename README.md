# helloworld
package com.mkyong;

import java.util.Map;

import javax.faces.bean.ManagedBean;
import javax.faces.bean.SessionScoped;
import javax.faces.context.FacesContext;

@ManagedBean(name="user")
@SessionScoped
public class UserBean{

	public String name;
	public String country;
	
	public String outcome(){
		
		FacesContext fc = FacesContext.getCurrentInstance();
		this.country = getCountryParam(fc);
		
		return "result";
	}

	//get value from "f:param"
	public String getCountryParam(FacesContext fc){
		
		Map<String,String> params = fc.getExternalContext().getRequestParameterMap();
		return params.get("country");
		
	}
	
	//getter and setter methods

}

