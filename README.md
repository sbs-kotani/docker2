# docker2
Docker環境へのアップ

git clone https://github.com/sbs-kotani/docker2.git                                             
git clone https://github.com/各自のgithub名/private_diary.git                            
python3 -m venv env                       
source env/bin/activate                                           

cd docker2                                 
docker-compose run django django-admin startproject private_diary .                        
sudo chown -R $USER:$USER .                         
docker-compose up                                            

cd ..                                                              
sudo chown -R $USER:$USER .                                                                 
cp -r private_diary/accounts docker2/src                                                     
cp -r private_diary/diary docker2/src                                                     
cp -r private_diary/media docker2/src                                                     
cp -r -f private_diary/private_diary docker2/src                                                     
cp -r private_diary/static docker2/src                                                     

cd docker2                                                     
nano src/private_diary/settings.py                                                     

		ALLOWED_HOSTS = ["*"]に変更
		DATABASESのHOST、PORT部を以下の値に変更する。
		'HOST': 'db',
		’PORT'： '5432',
		
docker-compose run django python3 ./manage.py makemigrations                                                     
docker-compose run django python3 ./manage.py migrate                                                     
sudo chown -R $USER:$USER .                                                     

docker-compose up                                                      

