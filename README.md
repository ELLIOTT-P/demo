# demo

 * getCompareList:(以list中第i个元素对list进行排序赋值). <br/>   
 * TODO(这里描述这个方法的注意事项 – 可选).<br/>  
 *  
 * @author wangjianbo  
 * @param list
 * @param i
 * @return  
 * @since JDK 1.8
 
private static List<List<String>> getCompareList(List<List<String>> list,int i){
	Map<String, Double> map = new TreeMap<>();
	for(List<String> listV : list) {
		String name = listV.get(0);
		Double score = Double.parseDouble(listV.get(i));
		map.put(name, score);
	}

	List<Entry<String, Double>> entry = new ArrayList<Entry<String, Double>>(map.entrySet());
	Collections.sort(entry, new Comparator<Entry<String, Double>>() {
		//升序
		public int compare(Entry<String, Double> o1, Entry<String, Double> o2) {
			return o2.getValue().compareTo(o1.getValue());
		}
	});

	//将其索引加一赋值给list中
	for(List<String> listV : list) {
		String name = listV.get(0);
		for(int a = 0 ; a < entry.size() ; a++) {
			String key = entry.get(a).getKey();
			if(key.equals(name)) {
				listV.set(i + 1, String.valueOf(a +1));
			}
		}
	}
	return list;
}
