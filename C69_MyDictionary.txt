package koreait.day16;

import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;
import java.util.Scanner;
import java.util.TreeMap;

public class C69_MyDictionary {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		
//		HashMap<String,String> my = new HashMap<>();
//		TreeMap<String, String> my = new TreeMap<>();
		List<Word> mywords = new ArrayList<>();		//my를 mywor로 바꿔서 구현해보기
		
		String English;
		String eng;
		String Korean;
		int level;
		boolean result = true;
		
		System.out.println("선택기능  →  1.단어저장    2.단어검색    3.전체보기    4. 레벨로 검색    5.프로그램 끝내기");
		

		while(result) {
			System.out.print("선택🙌 ->");
			int choice = sc.nextInt();
			
			switch(choice) {
			case 1:
				System.out.print("English -> ");
				English = sc.next();
				System.out.print("Korean -> ");
				Korean = sc.next();
				System.out.print("단어 level ? : ");				
				level = sc.nextInt();
				
				mywords.add(new Word(English, Korean,level));
				break;
			case 2:
				System.out.print("검색 단어  English -> ");
				eng = sc.next();
				
				for(Word temp : mywords) {
					if(temp.getEnglish().equals(eng)) {
						System.out.println("단어장 검색 완료했습니다 결과 ->  ");
						System.out.println(temp.toString());
					}
				}
			break;

			case 3:
//				System.out.print("단어장 전체보기 : "+mywords);
				all(mywords);		
				break;
			case 4:
				System.out.print("검색할 레벨 입력 (1~3) -> ");
				int no = sc.nextInt();
				level(mywords, no);
				
				break;
			case 5:
				result = false;
				break;
			default:
				System.out.println("번호를 잘못 입력하셨습니다");
				break;
			}
		}
		
		System.out.println("-------프로그램 종료--------");
	
		
		//참고 : 정수 데이터 입력을 받아야한다면 문자열 nextLine() 받아서 정수로 변환합니다.
		//		int score = Integer.parseInt(sc.nextLine());
		//이유 : nextInt()은 엔터를 처리하지 않아서 다음에 나오는 nextLine()에게 전달되어 입력 흐름에 방해가 됨
		
		
	}
	
	private static void level(List<Word> mywords, int no) {
		for(Word w : mywords) {
			if(w.getLevel() == no) {
				System.out.println(w);
			}
		}
	}




	private static void all(List<Word> mywords) {	
		mywords.sort(new Comparator<Word>(){		//비교할 요소가 2개 이상이므로 그냥하면 오류남
			@Override
			public int compare(Word o1, Word o2) {	// 오름차순 정렬
				return o1().compareTo(o2.getEnglish());
			}

		});
		
		System.out.println(String.format("%-20s %-20s %10s", "English","Korean","Level"));
		System.out.println("--------------------------------------------------------");
		for(Word w : mywords) {
			System.out.println(String.format("%-20s %-20s %10d", w.getEnglish(), w.getKorean(), w.getLevel()));
		}
		
		//System.out.println(String.format("%-20s %-20s %10s", "English","Korean","Level"));
//		System.out.println("-----------------------------------------------------------");
//		for(Word w:mywords)
//			System.out.println(String.format("-20s% %-20s %10d", w.getEnglish(), w.getKorean(), w.getLevel()));
	}	
}



	
	