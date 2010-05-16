class SeoBotParser

   require 'net/http'
   require 'uri'

   # attr accessors here

   #Konstruktor
   def initialize
   end

   #methods

   #read (file), zum logfile einlesen
   def read_file(path)
      if path != nil
         if File.exist?(path) then
            if File.readable?(path) then
               log = File.new(path, "r")
               @lines = log.readlines
               log.close
               return @lines
            else
               puts "File nicht lesbar!"
            end
         else
            puts "File existiert nicht!"
         end
      else
         puts "Bitte einen gültigen Dateipfad angeben!"
      end
   end

   #readURL(URL), um file aus URL einzulesen
   # funktioniert nicht, obwohl verschiedene Internetquellen genau so vorgehen
   def read_url(url)
      url_str = URI.parse(url)
      req = Net::HTTP::Get.new(url_str.path)
      http = Net::HTTP.new(url_str.host, url_str.port)
      res_zwei = http.request(req)
      #res = Net::HTTP.start(url_str.host, url_str.port) {|http|
          #http.request(req)}#{|res|
             #res.read_body do |segment|
             #print segment
             #puts "NExt segment" 
             #end
          #}
      #res_body = res.read_body
      #puts res_body.to_s
      #}
      puts res_zwei
   end

   #parse (array aus logfile lines, was immer aus dem txt wurde), zum logfile parsen
   def parse(log_lines, url_text)
      puts log_lines[0].to_s
      puts log_lines[1].to_s
      puts url_text.to_s
      # Lines splitten nach " - - " in IP und Text
      puts "attempt to split"
      separate_by = Regexp.new(' - - ')
      for i in 0...log_lines.length
         @temp = log_lines[i].split(separate_by)
         puts @temp[0].to_s
         puts @temp[1].to_s
      end
      # nach IP und Name prüfen
      # bei treffer print(Text)
   end

   #print (String)
   def print(text)
      puts text
   end

end

   sbp = SeoBotParser.new   

   #Pfad und Url
   log_path = "../log/apache-combined.log"
   google_url = "http://www.iplists.com/nw/google.txt"

   #ausfuehren
   line_array = sbp.read_file(log_path)
   google_text = sbp.read_url(google_url)
   sbp.parse(line_array, google_text)
