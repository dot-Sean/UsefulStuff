#!/bin/bash
#    Copyright (C) 2013 SferaDev

#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.

#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.

#    You should have received a copy of the GNU General Public License
#    along with this program.  If not, see <http://www.gnu.org/licenses/>

clear
echo "Welcome $USER"
echo
echo "What can I do for you?"
echo "Option 1: Repo sync"
echo "Option 2: Build clean"
echo "Option 3: Rebuild"
echo "Option 4: Create a changelog"
echo

read -p "Your option: " OPTION

case $OPTION in
"1")
echo "Repo syncing..."
repo sync -j20
;;
"2")
source build/envsetup.sh
lunch
rm -rf out/
read -p "Threads (usually 2-6): " THREADS
make illusion zip -j$THREADS
;;
"3")
source build/envsetup.sh
lunch
read -p "Threads (usually 2-6): " THREADS
make illusion zip -j$THREADS
;;
"4")
rm -rf ChangeLog
read -p "Since (YYYY-MM-DD): " CHANGELOG_DATE
repo forall -c git log --oneline --since={$CHANGELOG_DATE} --no-merges > ChangeLog
gedit ChangeLog
;;
esac

exit 0
