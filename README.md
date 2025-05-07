echo -e '#!/data/data/com.termux/files/usr/bin/bash
echo "🔒 بدأ التجميد لمدة 4 دقائق..."
termux-wake-lock  # يمنع قفل الشاشة
end=$((SECONDS+240))
trap "killall yes; termux-wake-unlock; echo ✅ انتهى التجميد" EXIT
while [ $SECONDS -lt $end ]; do
    yes > /dev/null &
done
killall yes
termux-wake-unlock
echo "✅ انتهى التجميد"' > freeze4min.sh

chmod +x freeze4min.sh && ./freeze4min.sh
